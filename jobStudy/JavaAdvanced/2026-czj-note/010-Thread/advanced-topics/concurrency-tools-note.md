# 并发工具类说明

## 1. 为什么这一份要单独补

线程这一章前面已经讲了：

- 线程基础
- 线程安全
- `synchronized`
- `volatile`
- `Lock`
- 线程池
- 并发容器

再往后，面试里很常继续追问：

- 你还知道哪些并发工具类？
- `CountDownLatch` 和 `CyclicBarrier` 有什么区别？
- `AtomicInteger` 是干什么的？
- `ThreadLocal` 是什么？

所以这一份主要是把线程章节后面的“并发工具类补充项”单独收进来。

## 2. 当前阶段最常见的并发工具类

这一阶段最值得先掌握的通常有：

1. `AtomicInteger`
2. `ThreadLocal`
3. `CountDownLatch`
4. `CyclicBarrier`
5. `Semaphore`

## 3. `AtomicInteger` 是什么

可以先粗理解成：

- 面向并发场景的原子整型类

它最常用来解决：

- 简单计数、自增、自减这类原子操作问题

### 3.1 为什么会需要它

因为前面已经讲过：

- `i++` 不是原子操作

如果只是想做一个线程安全的计数器，很多时候没有必要直接上重锁，`AtomicInteger` 往往更自然。

### 3.2 最常见写法

```java
AtomicInteger count = new AtomicInteger(0);
count.incrementAndGet();
```

### 3.3 适合什么场景

- 访问量计数
- 简单自增 ID
- 统计成功次数、失败次数

## 4. `ThreadLocal` 是什么

`ThreadLocal` 可以先理解成：

- 线程本地变量

也就是说：

- 每个线程拿到的是自己的那一份副本

所以它不是通过“共享数据再加锁”来解决问题，而是通过：

- 干脆不共享

来降低并发冲突。

### 4.1 常见场景

- 用户上下文
- TraceId
- 数据库连接上下文
- 每线程独立的格式化器或状态对象

### 4.2 面试里要注意

不要把 `ThreadLocal` 说成“线程安全类”本身，更准确的说法是：

- 它通过线程隔离的方式减少共享带来的并发问题

### 4.3 一个高频延伸点：`ThreadLocal` 的风险

面试里有时候还会继续追问：

- `ThreadLocal` 会不会有问题？

当前阶段可以先记住一个稳妥口径：

- 在线程池场景下，如果 `ThreadLocal` 用完不清理，可能带来脏数据和内存占用问题

所以更推荐的习惯是：

```java
try {
    threadLocal.set(value);
    // do something
} finally {
    threadLocal.remove();
}
```

你不需要一开始就把底层结构讲得很深，但至少要知道：

- `ThreadLocal` 不是放进去就不管了
- 在线程复用场景下，`remove()` 很重要

## 5. `CountDownLatch` 是什么

`CountDownLatch` 可以先粗理解成：

- 倒计时门闩

它最常见的语义是：

- 一个线程等待其他多个线程完成某件事

### 5.1 最常见用法

例如主线程要等 3 个子线程执行完：

```java
CountDownLatch latch = new CountDownLatch(3);
```

每个子线程完成后：

```java
latch.countDown();
```

主线程等待：

```java
latch.await();
```

### 5.2 适合什么场景

- 等多个初始化任务完成
- 等多个子任务都结束再汇总

### 5.3 一个简单业务例子

例如系统启动时，要同时完成：

- 配置加载
- 缓存预热
- 连接初始化

主线程不希望一个一个串行等，可以把这几个任务并发跑起来，然后用 `CountDownLatch` 等它们全部完成后再继续启动主流程。

## 6. `CyclicBarrier` 是什么

`CyclicBarrier` 可以先粗理解成：

- 循环栅栏

它强调的是：

- 一组线程都到齐后，再一起往下走

### 6.1 它和 `CountDownLatch` 的区别

这是高频题。

可以先这样记：

- `CountDownLatch` 更偏“一个等多个完成”
- `CyclicBarrier` 更偏“多个线程互相等到齐，再一起出发”

### 6.2 一个简单业务例子

例如有 3 个线程分别负责：

- 加载用户数据
- 加载订单数据
- 加载商品数据

如果要求它们都准备好后，再统一进入下一阶段处理，这种“都到齐再一起走”的味道就更像 `CyclicBarrier`。

## 7. `Semaphore` 是什么

`Semaphore` 可以先理解成：

- 信号量

它最典型的作用是：

- 控制同时访问某资源的线程数量

### 7.1 常见场景

例如：

- 只允许 3 个线程同时访问某个接口
- 只允许固定数量线程同时操作某个资源池

所以它不是单纯解决互斥，而是解决：

- 限流 / 限并发

### 7.2 一个更贴近业务的例子

例如某个外部接口很脆弱，你不希望瞬间有太多线程同时打过去，就可以用 `Semaphore` 控制：

- 同一时刻最多只允许 N 个线程访问

这在“限并发”这类题里很好用。

## 8. 这些工具类怎么区分

可以先按一句话记忆：

1. `AtomicInteger`
   适合原子计数
2. `ThreadLocal`
   适合线程隔离
3. `CountDownLatch`
   适合一个线程等多个线程完成
4. `CyclicBarrier`
   适合多个线程互相等待到齐再一起走
5. `Semaphore`
   适合限制同时访问资源的线程数量

## 9. 为什么 `AtomicInteger` 不是“万能计数器”

`AtomicInteger` 很适合简单原子计数，但它也不是万能的。

如果你的逻辑变成：

1. 先判断
2. 再更新
3. 还要和别的状态一起修改

这种多步骤复合操作，就不能只靠单个原子类名义上“线程安全”来偷懒。

所以更稳妥的理解是：

- 它适合简单原子操作
- 复杂复合逻辑仍然要谨慎设计

## 10. 面试里最常被问的主线

这一块在面试里高频通常集中在：

1. `AtomicInteger` 为什么能解决简单计数问题
2. `ThreadLocal` 是什么
3. `CountDownLatch` 和 `CyclicBarrier` 区别
4. `Semaphore` 是干什么的
5. `ThreadLocal` 用完为什么最好 `remove()`

## 11. 面试里最容易漏的点

### 10.1 只记得类名，不知道场景

这是最常见的问题。

一定要把：

- 工具类
- 使用场景

对应起来。

### 10.2 把 `CountDownLatch` 和 `CyclicBarrier` 混在一起

要记住：

- 一个偏等待完成
- 一个偏到齐出发

### 10.3 把 `ThreadLocal` 当成“加锁工具”

这不准确。

更准确地说：

- 它是通过线程隔离来减少共享冲突

### 10.4 只会背 `AtomicInteger`，不会说边界

也要知道：

- 它更适合简单原子计数
- 复杂复合逻辑不一定只靠它就够

## 12. 面试里怎么回答比较稳

如果面试官问：

- 你还知道哪些并发工具类？

可以这样答：

除了基础的 `synchronized`、`volatile` 和 `Lock`，Java 里还常见一些并发工具类，比如 `AtomicInteger` 适合做原子计数，`ThreadLocal` 适合做线程隔离，`CountDownLatch` 常用于一个线程等待多个线程完成任务，`CyclicBarrier` 适合一组线程到齐后再一起往下执行，`Semaphore` 则常用于限制并发访问资源的数量。

如果继续追问 `CountDownLatch` 和 `CyclicBarrier` 的区别，可以直接补一句：

- 一个更像“等大家做完”
- 一个更像“等大家到齐再一起走”

## 13. 当前阶段最该记住的结论

1. 并发工具类不是越多越好，先记住场景最重要
2. `AtomicInteger` 适合简单原子计数
3. `ThreadLocal` 适合线程隔离
4. `CountDownLatch` 和 `CyclicBarrier` 是高频区别题
5. `Semaphore` 更偏限流和限并发

## 14. 一句话总结

并发工具类这一块，最重要的不是把所有类名都背下来，而是先分清：它是解决计数、线程隔离、等待协作，还是限制并发数量。
