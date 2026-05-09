# 线程复盘 Checklist

## 1. 这一份怎么用

这一份不是知识点详解，而是线程这一章的最终复盘清单。

适合用法：

- 学完整章后做自查
- 面试前最后快速过一遍
- 找出自己还答不顺的点

你可以把每一条都当成一个问题去问自己：

- 我能不能自己讲清楚？
- 我能不能举个简单例子？
- 我能不能区分相近概念？

## 2. 基础概念 Checklist

- 我能讲清楚什么是进程、什么是线程
- 我能讲清楚为什么要有多线程
- 我能讲清楚并发和并行的区别
- 我能讲清楚 CPU 调度和上下文切换的大概含义
- 我能讲清楚为什么线程太多反而可能更慢
- 我知道协程是什么，也知道它在线程基础阶段不是第一重点

## 3. 线程创建 Checklist

- 我知道创建线程常见有哪几种方式
- 我能写出继承 `Thread` 的基础写法
- 我能写出实现 `Runnable` 的基础写法
- 我能讲清楚为什么 `Runnable` 比直接继承 `Thread` 更常用
- 我能讲清楚 `Callable` 和 `Runnable` 的区别
- 我知道 `Future` / `FutureTask` 是干什么的
- 我能讲清楚为什么生产环境更推荐线程池，而不是频繁 `new Thread()`

## 4. 状态与方法 Checklist

- 我知道 Java 线程常见的 6 种状态
- 我能讲清楚 `NEW`、`RUNNABLE`、`BLOCKED`、`WAITING`、`TIMED_WAITING`、`TERMINATED`
- 我知道 `RUNNABLE` 不等于一定正在运行
- 我能讲清楚 `run()` 和 `start()` 的区别
- 我知道 `join()` 的作用
- 我知道 `yield()` 是让出 CPU 提示，不保证一定生效
- 我知道 `isAlive()` 用来判断线程是否还存活

## 5. 协作方法 Checklist

- 我能讲清楚 `sleep()` 和 `wait()` 的区别
- 我知道 `sleep()` 属于 `Thread`
- 我知道 `wait()` 属于 `Object`
- 我知道 `sleep()` 不释放锁
- 我知道 `wait()` 会释放锁
- 我能讲清楚为什么 `wait()` 必须在同步代码块中使用
- 我能讲清楚 `notify()` 和 `notifyAll()` 的区别
- 我知道 `join()` 的核心是“当前线程等待目标线程结束”

## 6. 线程安全 Checklist

- 我能讲清楚什么是线程安全
- 我知道线程安全问题通常需要“共享资源 + 并发访问”这两个条件
- 我能讲清楚为什么 `i++` 在并发下不安全
- 我知道什么是竞态条件
- 我能讲清楚原子性
- 我能讲清楚可见性
- 我能讲清楚有序性
- 我知道线程安全不等于只有加锁这一种思路

## 7. `synchronized` Checklist

- 我能讲清楚什么是 `synchronized`
- 我知道 `synchronized` 的三种常见写法
- 我知道同步实例方法锁的是 `this`
- 我知道同步静态方法锁的是 `Class` 对象
- 我知道同步代码块锁的是括号里的对象
- 我能讲清楚为什么 `synchronized(new Object())` 往往起不到预期同步效果
- 我知道 `synchronized` 的核心是控制临界区互斥访问
- 我能讲清楚它和原子性、可见性、有序性的关系

## 8. `volatile` Checklist

- 我能讲清楚什么是 `volatile`
- 我知道 `volatile` 最核心解决的是可见性
- 我知道 `volatile` 还能保证一定程度上的有序性
- 我知道 `volatile` 不能直接保证复合操作的原子性
- 我能讲清楚为什么 `volatile` 不能保证 `i++` 线程安全
- 我知道停止标记是 `volatile` 的经典场景
- 我能讲清楚 `volatile` 和 `synchronized` 的侧重点不同

## 9. `Lock / ReentrantLock` Checklist

- 我能讲清楚为什么 Java 还提供了 `Lock`
- 我知道 `Lock` 和 `synchronized` 的目标类似，但控制方式不同
- 我能写出 `lock()` + `try` + `finally` + `unlock()` 的标准结构
- 我知道为什么 `unlock()` 一般必须放在 `finally`
- 我能讲清楚什么是可重入
- 我知道 `ReentrantLock` 是常见的显式可重入锁
- 我知道 `tryLock()` 的作用
- 我知道 `lockInterruptibly()` 是可中断获取锁
- 我知道公平锁和非公平锁的大概区别

## 10. 线程池 Checklist

- 我能讲清楚为什么不推荐频繁 `new Thread()`
- 我能讲清楚什么是线程池
- 我知道线程池的三大核心价值：线程复用、控制并发数量、统一管理任务
- 我知道 `Executor`、`ExecutorService`、`ThreadPoolExecutor` 的层次
- 我能讲清楚 `execute()` 和 `submit()` 的区别
- 我知道 `submit()` 会返回 `Future`
- 我知道线程池的核心参数有哪些
- 我能讲清楚线程池任务流转的大致过程
- 我知道常见拒绝策略有哪些
- 我能讲清楚为什么不建议无脑使用 `Executors` 默认工厂

## 11. 并发容器 Checklist

- 我知道为什么普通集合在并发环境下容易出问题
- 我知道 `ArrayList`、`HashMap` 等普通集合不是线程安全的
- 我能讲清楚什么是并发容器
- 我知道 `ConcurrentHashMap` 是最常见的线程安全 `Map`
- 我能讲清楚为什么 `ConcurrentHashMap` 比 `Hashtable` 更常用
- 我知道 `CopyOnWriteArrayList` 更适合读多写少场景
- 我知道 `BlockingQueue` 非常适合生产者消费者和任务缓冲
- 我知道并发容器不是万能的，复合操作依然要小心

## 12. 面试表达 Checklist

- 我能用自己的话讲清楚“线程这一章的主线”
- 我能顺着讲出：线程基础 -> 状态方法 -> 线程安全 -> 同步手段 -> 线程池 -> 并发容器
- 我能回答高频区别题：
- `run()` vs `start()`
- `sleep()` vs `wait()`
- `Runnable` vs `Callable`
- `synchronized` vs `volatile`
- `synchronized` vs `Lock`
- `execute()` vs `submit()`
- 我能举出至少 2 个简单例子：
- `i++`
- 卖票
- 停止标记
- 线程池提交任务

## 13. 面试前 10 分钟压缩版

如果只剩最后 10 分钟，优先确认自己能顺畅口述这些点：

1. 进程和线程的区别
2. 创建线程有哪几种方式
3. `run()` 和 `start()` 的区别
4. `sleep()` 和 `wait()` 的区别
5. 什么是线程安全
6. 为什么 `i++` 不安全
7. `synchronized` 锁的是什么
8. `volatile` 为什么不能保证 `i++`
9. 为什么要用线程池
10. 线程池核心参数和任务流转过程
11. `ConcurrentHashMap` 为什么比 `Hashtable` 更常用

## 14. 一句话总结

线程这一章最后复盘时，最重要的不是看自己背了多少类名，而是看自己能不能把“为什么会出问题、Java 怎么解决、实际开发怎么用”这条主线完整讲顺。
