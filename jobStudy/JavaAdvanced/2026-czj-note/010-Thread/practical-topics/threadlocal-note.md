# `ThreadLocal` 补充笔记

## 1. 为什么这一份要单独补

在线程这一章里，`ThreadLocal` 很容易被单独追问。

原因通常有两个：

- 它经常和“线程安全”一起出现
- 它又经常和“内存泄漏”“线程池复用”一起出现

所以这一份不是只讲 API，而是要把下面几件事讲顺：

- `ThreadLocal` 是干什么的
- 它为什么能做到“线程隔离”
- 为什么在线程池里使用时要特别小心

## 2. 先一句话理解 `ThreadLocal`

可以先记一个口径：

- `ThreadLocal` 不是用来解决多个线程抢同一个变量，而是给每个线程单独准备一份变量副本

也就是说，它更像：

- 线程自己的本地存储

而不是：

- 多个线程共享同一份数据

## 3. `ThreadLocal` 到底是干什么的

它最常见的作用是：

- 在同一个线程执行链路里，存一份当前线程独有的数据

常见例子包括：

- 用户上下文
- 请求追踪 ID
- 数据库连接上下文
- 格式化工具的线程隔离

所以你可以粗理解成：

- `ThreadLocal` 用空间换隔离

## 4. 为什么它能做到线程隔离

因为不是把值直接存在 `ThreadLocal` 对象本身里，而是：

- 每个线程对象内部都有一份和 `ThreadLocal` 相关的存储结构

所以同一个 `ThreadLocal`：

- 在线程 A 里取到的是 A 自己存的值
- 在线程 B 里取到的是 B 自己存的值

这就是它能做到“同名变量，不同线程各用各的”的核心原因。

## 5. `ThreadLocal` 最常用的几个方法

当前阶段先记这几个就够了：

1. `set()`
2. `get()`
3. `remove()`
4. `initialValue()`

### 5.1 `set()`

- 给当前线程存值

### 5.2 `get()`

- 取当前线程自己的值

### 5.3 `remove()`

- 删除当前线程里这份值

### 5.4 `initialValue()`

- 当前线程第一次获取时，如果还没有值，可以给一个初始值

## 6. 一个最基础的理解例子

```java
private static final ThreadLocal<String> LOCAL = new ThreadLocal<>();

public static void main(String[] args) {
    Thread t1 = new Thread(() -> {
        LOCAL.set("A");
        System.out.println(Thread.currentThread().getName() + ": " + LOCAL.get());
        LOCAL.remove();
    });

    Thread t2 = new Thread(() -> {
        LOCAL.set("B");
        System.out.println(Thread.currentThread().getName() + ": " + LOCAL.get());
        LOCAL.remove();
    });

    t1.start();
    t2.start();
}
```

这个例子里，两个线程都用同一个 `ThreadLocal`，但拿到的值不会互相干扰。

## 7. `ThreadLocal` 和同步锁有什么区别

这是很高频的追问。

可以先粗分成：

- 锁是在控制共享资源怎么安全访问
- `ThreadLocal` 是在避免线程之间共享同一份数据

也就是说：

- 如果问题是“多个线程都要改同一份数据”，更常想到锁
- 如果问题是“每个线程都需要一份自己的上下文”，更常想到 `ThreadLocal`

## 8. `ThreadLocalMap` 要掌握到什么程度

当前阶段不需要背源码级细节，但要知道一个粗框架：

- 每个线程内部都有一个 `ThreadLocalMap`
- `ThreadLocal` 本身更像访问这个 Map 的 key
- 当前线程的数据是放在这个 Map 里的

面试里能说到这一层通常已经够用了。

## 9. 为什么常说 `ThreadLocal` 可能导致内存泄漏

这是最经典的问题之一。

你至少要先记住这一条主线：

- `ThreadLocalMap` 里的 key 是弱引用，但 value 不是弱引用

这会带来什么问题？

- 如果外部对 `ThreadLocal` 对象本身没有强引用了，key 可能被回收
- 但 value 还可能挂在当前线程的 `ThreadLocalMap` 里

如果这个线程又长期不结束，那这份 value 就可能一直残留。

所以大家才会说：

- `ThreadLocal` 使用不当可能带来内存泄漏风险

## 10. 为什么在线程池里问题更明显

因为线程池里的线程不是用完就销毁，而是会被复用。

这会带来两个高频风险：

1. 旧值残留
2. 请求间数据污染

比如：

- 请求 A 在线程里放了用户信息
- 但执行完没有 `remove()`
- 后面线程被复用给请求 B
- 那请求 B 就可能读到请求 A 的残留数据

所以线程池环境里，`ThreadLocal` 的风险会更真实。

## 11. 为什么一般都强调 finally 里 `remove()`

因为你不能只指望：

- 请求一定正常结束

如果中途异常了，但没有清理，那线程复用时问题就会留下来。

所以一个很稳的写法是：

```java
try {
    CONTEXT.set(userId);
    // 业务逻辑
} finally {
    CONTEXT.remove();
}
```

这也是面试里非常推荐直接说出来的一句。

## 12. `ThreadLocal` 适合哪些场景

常见适用场景：

1. 保存当前请求上下文
2. 保存用户身份信息
3. 保存链路追踪 ID
4. 保存每线程独立对象

但它不适合干的事情也要知道：

- 不适合在线程之间传递共享数据
- 不适合替代正常的参数传递设计
- 不适合到处滥用，导致上下文来源不清晰

## 13. `InheritableThreadLocal` 是什么

可以先粗理解成：

- 子线程创建时，可以拿到父线程里的值副本

但要注意：

- 它更像“创建子线程时复制一份”
- 不等于后续父子线程之间自动同步变化

当前阶段知道这个边界就够用了。

## 14. `TransmittableThreadLocal` 是什么

这个点更偏扩展。

可以先记成：

- 它是为了解决线程池复用场景下，普通 `ThreadLocal` / `InheritableThreadLocal` 上下文传递不自然的问题

也就是说：

- 在线程池里任务不是“新建子线程”
- 所以单纯靠 `InheritableThreadLocal` 往往不够

很多项目里会用 TTL 这类方案去做上下文透传。

## 15. 面试里怎么回答“`ThreadLocal` 是什么”

可以直接背一版：

`ThreadLocal` 可以理解成线程本地变量，它不是让多个线程安全地共享一份数据，而是给每个线程单独准备一份变量副本。它常用来保存当前线程上下文，比如用户信息、请求 ID 之类的数据。

## 16. 面试里怎么回答“为什么会内存泄漏”

可以直接背一版：

`ThreadLocalMap` 里的 key 是弱引用，value 不是弱引用。如果 `ThreadLocal` 对象本身没有外部强引用了，key 可能被回收，但 value 还可能挂在线程对象内部的 Map 里。尤其在线程池这种线程长期复用的场景里，如果不及时 `remove()`，就容易出现 value 残留和内存泄漏风险。

## 17. 面试里怎么回答“为什么在线程池里一定要注意 `remove()`”

可以直接背一版：

因为线程池里的线程会被复用，不会像普通短生命周期线程那样很快销毁。如果上一个任务把数据放进了 `ThreadLocal`，执行完又没清理，下一个任务复用这个线程时就可能读到旧值，所以一般会放在 `finally` 里做 `remove()`。

## 18. 当前阶段最值得记什么

这一份最少要记住：

1. `ThreadLocal` 是线程隔离，不是线程共享
2. 它常用来保存线程上下文
3. 它不是用来替代锁的
4. `ThreadLocalMap` 的 key 是弱引用，value 可能残留
5. 在线程池里要特别注意 `finally + remove()`
6. `InheritableThreadLocal` 和 TTL 只要先会粗理解即可

## 19. 一句话总结

`ThreadLocal` 这块面试最核心的不是 API，而是三句话：

- 它是干什么的
- 它为什么会有泄漏风险
- 为什么在线程池里要及时清理
