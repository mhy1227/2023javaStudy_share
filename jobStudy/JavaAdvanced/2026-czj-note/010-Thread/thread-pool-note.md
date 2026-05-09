# 线程池说明

## 1. 为什么线程这一章要讲线程池

因为实际开发里，线程这块通常不会停留在：

- 会创建线程
- 会加锁

面试官更关心的是：

- 你知不知道为什么不能在业务里到处 `new Thread()`
- 你知不知道线程该怎么统一管理

这时线程池就一定会被问到。

所以线程池这一份，核心不是只背类名，而是先讲清楚：

- 为什么需要线程池
- 线程池解决什么问题
- 线程池怎么配置
- 面试里最常问哪些参数和坑

## 2. 什么是线程池

可以先给一个容易口述的定义：

- 线程池是一种对线程进行复用和统一管理的机制，它会预先或按需创建一批线程，用来执行提交进来的任务

更直白一点说：

- 不是每来一个任务就新建一个线程
- 而是把任务交给一组可复用的线程去处理

## 3. 为什么不推荐频繁 `new Thread()`

这是线程池最核心的前置问题。

频繁手动创建线程的问题主要有：

1. 创建和销毁线程有成本
2. 线程过多会增加调度开销和上下文切换成本
3. 不方便统一管理线程数量
4. 不方便控制任务堆积
5. 程序容易因为线程失控而出现资源问题

所以面试里可以先记住一句很稳的话：

- 线程池的核心价值之一就是复用线程，减少频繁创建和销毁线程的成本

## 4. 线程池主要解决什么问题

线程池主要解决三类问题：

### 4.1 线程复用

线程用完不马上销毁，可以继续执行后续任务。

### 4.2 控制并发数量

不会无限制地创建线程，避免线程数量失控。

### 4.3 统一管理任务

可以配合任务队列、拒绝策略、监控参数来管理任务执行。

## 5. 线程池最常见的接口和类

当前阶段先记住这几层：

1. `Executor`
2. `ExecutorService`
3. `ThreadPoolExecutor`

### 5.1 `Executor`

偏顶层接口，定义了最基本的任务执行能力。

### 5.2 `ExecutorService`

是在 `Executor` 基础上扩展出来的更常用接口，支持：

- 提交任务
- 关闭线程池
- 返回结果等

### 5.3 `ThreadPoolExecutor`

这是最核心、最常被展开讲的线程池实现类。

面试里如果说线程池参数，通常讲的就是它。

## 6. 最基础的线程池写法

```java
ExecutorService executorService = Executors.newFixedThreadPool(3);

executorService.execute(() -> {
    System.out.println(Thread.currentThread().getName() + " running");
});

executorService.shutdown();
```

这个写法适合入门理解线程池用法。

但面试里不能只停在这里，因为后面往往会追问：

- 为什么不建议无脑用 `Executors`

## 7. `execute()` 和 `submit()` 的区别

这是高频问题。

### 7.1 `execute()`

主要用来提交不需要返回值的任务。

### 7.2 `submit()`

可以提交有返回值或无返回值任务，并返回 `Future`。

例如：

```java
ExecutorService executorService = Executors.newFixedThreadPool(3);

Future<Integer> future = executorService.submit(() -> 100);
Integer result = future.get();
```

### 7.3 面试里怎么答

可以先这样说：

- `execute()` 更简单，偏执行任务
- `submit()` 更灵活，可以拿到 `Future`，便于获取结果或处理异常

## 8. `ThreadPoolExecutor` 的核心参数

这是线程池最重要的部分之一。

最常见构造参数有这几个：

1. `corePoolSize`
2. `maximumPoolSize`
3. `keepAliveTime`
4. `unit`
5. `workQueue`
6. `threadFactory`
7. `handler`

## 9. `corePoolSize` 是什么

核心线程数。

可以先粗理解成：

- 线程池平时最基本保留的线程数量

## 10. `maximumPoolSize` 是什么

最大线程数。

可以理解成：

- 在线程池压力增大时，线程数量最多能扩到多少

## 11. `keepAliveTime` 是什么

空闲线程存活时间。

主要用于：

- 非核心线程空闲多久后可以被回收

## 12. `workQueue` 是什么

任务队列。

作用是：

- 当核心线程都忙时，新任务先尝试进入队列等待

所以线程池并不是一来任务就马上不停建新线程。

## 13. `threadFactory` 是什么

线程工厂。

作用主要是：

- 控制线程怎么被创建
- 比如线程名、线程属性等

实际开发里常用来自定义线程名称，便于排查问题。

## 14. `handler` 是什么

拒绝策略。

当任务太多，线程池和队列都扛不住时，就要决定：

- 这个新任务怎么办

## 15. 线程池处理任务的大致流程

这一段很重要，建议按顺序记。

可以先粗记为：

1. 如果当前线程数小于核心线程数，优先创建核心线程执行任务
2. 如果核心线程满了，任务先进入队列
3. 如果队列也满了，且线程数还没到最大线程数，再创建非核心线程
4. 如果队列满了、线程也到上限了，就触发拒绝策略

这条流程基本就是面试里线程池参数题的主线。

## 16. 常见拒绝策略

`ThreadPoolExecutor` 常见拒绝策略有：

1. `AbortPolicy`
2. `CallerRunsPolicy`
3. `DiscardPolicy`
4. `DiscardOldestPolicy`

### 16.1 `AbortPolicy`

直接抛异常。

### 16.2 `CallerRunsPolicy`

由提交任务的调用线程自己执行这个任务。

### 16.3 `DiscardPolicy`

直接丢弃任务，不抛异常。

### 16.4 `DiscardOldestPolicy`

丢掉队列中最老的任务，再尝试提交当前任务。

## 17. 为什么不建议无脑用 `Executors` 默认工厂

这是非常高频的一题。

很多教程里都直接写：

- `Executors.newFixedThreadPool()`
- `Executors.newCachedThreadPool()`

但面试里更常见的说法是：

- 不建议生产环境无脑使用 `Executors` 默认工厂，而更推荐直接使用 `ThreadPoolExecutor`

原因核心在于：

- 默认工厂屏蔽了关键参数
- 不同工厂可能带来队列过长或线程数失控等风险

当前阶段你可以先稳妥地说：

- 直接使用 `ThreadPoolExecutor` 更方便显式控制核心线程数、最大线程数、队列和拒绝策略

## 18. 一个更完整的线程池示例

```java
ThreadPoolExecutor executor = new ThreadPoolExecutor(
        2,
        4,
        60,
        TimeUnit.SECONDS,
        new LinkedBlockingQueue<>(10),
        Executors.defaultThreadFactory(),
        new ThreadPoolExecutor.AbortPolicy()
);

executor.execute(() -> {
    System.out.println(Thread.currentThread().getName() + " running");
});

executor.shutdown();
```

这个例子里你至少要会解释：

- 核心线程数是 2
- 最大线程数是 4
- 队列容量是 10
- 拒绝策略是抛异常

## 19. 线程池的优点

面试里可以先记这几条：

1. 复用线程，降低创建销毁成本
2. 控制并发线程数量
3. 统一管理任务执行
4. 可以配置队列和拒绝策略
5. 更适合生产环境

## 20. 线程池的风险点

线程池不是有了就万事大吉。

它也有风险点：

1. 参数配错可能造成资源浪费
2. 队列太大可能积压任务
3. 最大线程数太大可能压垮系统
4. 忘记关闭线程池会有资源问题
5. 拒绝策略没想清楚可能导致任务丢失或异常

## 21. 面试里最容易漏的点

### 21.1 只会说线程池是“为了提高性能”

这太虚了。

至少要补完整：

- 线程复用
- 控制并发数量
- 统一管理任务

### 21.2 只会背核心线程数和最大线程数

但说不清任务处理流程。

一定要把：

- 核心线程
- 队列
- 非核心线程
- 拒绝策略

串起来。

### 21.3 只会用 `Executors`，不会解释为什么不推荐

这在面试里很容易被追问。

### 21.4 只会说 `submit()` 能返回结果

但不会说它返回的是：

- `Future`

## 22. 面试里怎么回答“为什么要用线程池”

可以这样答：

线程池主要是为了复用线程、减少频繁创建和销毁线程的成本，同时统一管理线程数量和任务执行过程，避免线程数量失控。相比手动频繁 `new Thread()`，线程池更适合生产环境，也更方便结合任务队列和拒绝策略做整体控制。

## 23. 面试里怎么回答“线程池核心参数有哪些”

可以这样答：

`ThreadPoolExecutor` 常见核心参数包括核心线程数 `corePoolSize`、最大线程数 `maximumPoolSize`、空闲线程存活时间 `keepAliveTime`、时间单位 `unit`、任务队列 `workQueue`、线程工厂 `threadFactory` 和拒绝策略 `handler`。线程池处理任务时通常会先用核心线程，核心线程满后进队列，队列满后再尝试扩容到最大线程数，超出后再触发拒绝策略。

## 24. 当前阶段最该记住的结论

1. 线程池的核心价值是复用线程和统一管理任务
2. 不建议频繁手动 `new Thread()`
3. `execute()` 偏执行任务，`submit()` 可配合 `Future` 获取结果
4. 线程池最关键的是参数和任务流转过程
5. 生产环境更推荐显式使用 `ThreadPoolExecutor`

## 25. 一句话总结

线程池这一块最重要的不是死背几个 API，而是先讲清楚：为什么线程不能乱建、线程池如何复用和管理线程、任务是怎么流转的，以及为什么生产环境更强调显式配置而不是无脑用默认工厂。
