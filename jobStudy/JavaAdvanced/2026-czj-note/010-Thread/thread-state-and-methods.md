# 线程状态与常用方法

## 1. 为什么这一份很重要

线程状态这一块，经常被低估。

很多人会创建线程，也知道 `run()`、`start()`，但一旦问到：

- 线程有哪些状态？
- `RUNNABLE` 是不是就等于正在运行？
- `join()` 是做什么的？
- `yield()` 有什么用？

就容易答得很虚。

所以这一份的重点是：

1. 把线程状态讲清楚
2. 把常见方法和状态变化联系起来
3. 把面试里最容易混的点挑出来

## 2. Java 线程的 6 种状态

Java 里线程状态通常指 `Thread.State` 里的 6 种：

1. `NEW`
2. `RUNNABLE`
3. `BLOCKED`
4. `WAITING`
5. `TIMED_WAITING`
6. `TERMINATED`

## 3. `NEW`

`NEW` 表示：

- 线程对象已经创建
- 但还没有调用 `start()`

例如：

```java
Thread t = new Thread(() -> System.out.println("run"));
```

这时线程对象已经有了，但线程还没真正启动。

## 4. `RUNNABLE`

`RUNNABLE` 是最容易误解的状态。

它并不简单等于：

- 正在运行

更准确地说，它表示：

- 线程已经具备运行条件
- 可能正在运行
- 也可能正在等待 CPU 时间片

所以面试里要特别注意一句：

- `RUNNABLE` 包含“就绪”和“运行中”这两类情况

## 5. `BLOCKED`

`BLOCKED` 通常表示：

- 线程在等待获取某个监视器锁

最常见场景是：

- 进入 `synchronized` 代码块时，锁已经被别的线程占用

这时线程会进入 `BLOCKED` 状态。

## 6. `WAITING`

`WAITING` 表示：

- 线程进入无限期等待
- 需要等待其他线程显式唤醒

典型方法：

- `Object.wait()`
- `Thread.join()`

## 7. `TIMED_WAITING`

`TIMED_WAITING` 表示：

- 线程进入带时间限制的等待状态

典型方法：

- `Thread.sleep(long millis)`
- `Object.wait(long timeout)`
- `Thread.join(long millis)`

## 8. `TERMINATED`

`TERMINATED` 表示：

- 线程已经执行结束

也就是 `run()` 方法执行完毕后，线程进入终止状态。

## 9. 线程状态变化的简化理解

可以先按这条主线记：

```text
NEW
  -> start()
RUNNABLE
  -> 获取不到锁，可能进入 BLOCKED
  -> wait()/join()，可能进入 WAITING
  -> sleep()/wait(timeout)/join(timeout)，可能进入 TIMED_WAITING
  -> run() 执行结束，进入 TERMINATED
```

## 10. 常见方法一：`start()`

### 10.1 作用

`start()` 用来真正启动线程。

调用后，线程会从 `NEW` 进入可运行状态。

### 10.2 常见误区

- `start()` 不是直接执行 `run()` 的普通方法
- 一个线程对象通常不能重复 `start()`

## 11. 常见方法二：`run()`

### 11.1 作用

`run()` 里写的是线程要执行的任务逻辑。

### 11.2 常见误区

直接调用 `run()` 只是普通方法调用，不会创建新线程。

## 12. 常见方法三：`currentThread()`

`Thread.currentThread()` 用来获取当前正在执行的线程对象。

例如：

```java
System.out.println(Thread.currentThread().getName());
```

这个方法在调试线程执行时很常见。

## 13. 常见方法四：`getName()` / `setName()`

这两个方法主要用于：

- 给线程命名
- 打印日志时更容易区分线程

面试里不是特别高频，但实际排查问题时很常用。

## 14. 常见方法五：`join()`

`join()` 的核心作用是：

- 让当前线程等待目标线程执行结束

简单例子：

```java
Thread t = new Thread(() -> {
    System.out.println("child thread");
});

t.start();
t.join();
System.out.println("main thread continue");
```

可以这样理解：

- 主线程会等 `t` 执行完，再继续往下走

## 15. 常见方法六：`yield()`

`yield()` 的作用可以粗理解成：

- 当前线程主动让出一次 CPU 使用机会

但要注意：

- 它只是提示调度器“我可以先让一下”
- 不保证一定会生效

所以面试里不用把它说得太重。

## 16. 常见方法七：`isAlive()`

`isAlive()` 用来判断线程是否还存活。

大致可以理解为：

- 已经启动且还没执行结束，通常返回 `true`

## 17. 面试里这一块最容易混的点

### 17.1 `RUNNABLE` 不等于“正在执行”

这是高频易错点。

要记住：

- `RUNNABLE` 既可能在跑
- 也可能只是准备好在等 CPU

### 17.2 `BLOCKED`、`WAITING`、`TIMED_WAITING` 容易混

可以这样粗分：

- `BLOCKED`：等锁
- `WAITING`：无限等别人唤醒
- `TIMED_WAITING`：带时间限制地等

### 17.3 只会背状态名，不会和方法对应起来

比如：

- `sleep()` 常对应 `TIMED_WAITING`
- `wait()` 常对应 `WAITING`
- 进同步块拿不到锁常对应 `BLOCKED`

## 18. 面试里怎么回答“线程有哪些状态”

可以这样答：

Java 线程状态通常有 6 种，分别是 `NEW`、`RUNNABLE`、`BLOCKED`、`WAITING`、`TIMED_WAITING` 和 `TERMINATED`。其中 `NEW` 是创建但未启动，`RUNNABLE` 表示具备运行条件，`BLOCKED` 主要是等锁，`WAITING` 是无限期等待其他线程唤醒，`TIMED_WAITING` 是带超时的等待，`TERMINATED` 是线程执行结束。

## 19. 当前阶段最该记住的结论

1. Java 线程有 6 种状态
2. `RUNNABLE` 不只是“正在运行”
3. `BLOCKED` 主要和锁竞争有关
4. `WAITING` 和 `TIMED_WAITING` 的区别在于是否带超时
5. 线程方法要和状态变化一起理解

## 20. 一句话总结

线程状态这一块，核心不是背 6 个英文单词，而是要能把“线程处于什么阶段、为什么进入这个状态、哪些方法会导致状态变化”串起来。
