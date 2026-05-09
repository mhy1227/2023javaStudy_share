# 线程与并发族谱

## 1. 为什么这一章也要先看族谱

线程这块如果一上来就直接看：

- `Thread`
- `Runnable`
- `Callable`
- `Future`
- `synchronized`
- `Lock`
- 线程池

很容易出现的问题是：

- 类名都认识
- 方法也看过
- 但脑子里没有结构

所以这里还是先把整体知识地图搭起来。

## 2. 简版族谱

```text
线程与并发
├─ 线程基础
│  ├─ 进程与线程
│  ├─ 并发与并行
│  ├─ 线程创建
│  └─ 线程生命周期
├─ 线程协作
│  ├─ sleep
│  ├─ wait / notify / notifyAll
│  └─ join
├─ 线程安全
│  ├─ 原子性
│  ├─ 可见性
│  └─ 有序性
├─ 锁与同步
│  ├─ synchronized
│  ├─ volatile
│  ├─ Lock
│  └─ ReentrantLock
├─ 任务执行
│  ├─ Callable
│  ├─ Future
│  └─ 线程池
└─ 并发容器
   ├─ ConcurrentHashMap
   ├─ CopyOnWriteArrayList
   └─ BlockingQueue
```

## 3. 详细版族谱

```text
线程与并发
├─ 一、基础认知
│  ├─ 1. 进程
│  ├─ 2. 线程
│  ├─ 3. 并发
│  ├─ 4. 并行
│  └─ 5. 上下文切换
├─ 二、线程创建
│  ├─ 1. 继承 Thread
│  ├─ 2. 实现 Runnable
│  ├─ 3. 实现 Callable
│  ├─ 4. 配合 Future / FutureTask
│  └─ 5. 线程池提交任务
├─ 三、线程状态与常用方法
│  ├─ 1. NEW
│  ├─ 2. RUNNABLE
│  ├─ 3. BLOCKED
│  ├─ 4. WAITING
│  ├─ 5. TIMED_WAITING
│  ├─ 6. TERMINATED
│  ├─ 7. start()
│  ├─ 8. run()
│  ├─ 9. sleep()
│  ├─ 10. yield()
│  └─ 11. join()
├─ 四、线程通信与协作
│  ├─ 1. wait()
│  ├─ 2. notify()
│  ├─ 3. notifyAll()
│  ├─ 4. 生产者消费者
│  └─ 5. 共享变量通知
├─ 五、并发核心问题
│  ├─ 1. 原子性
│  ├─ 2. 可见性
│  ├─ 3. 有序性
│  ├─ 4. 竞态条件
│  └─ 5. 死锁
├─ 六、同步与锁
│  ├─ 1. synchronized
│  ├─ 2. synchronized 锁对象
│  ├─ 3. synchronized 锁方法
│  ├─ 4. synchronized 锁类
│  ├─ 5. volatile
│  ├─ 6. Lock
│  ├─ 7. ReentrantLock
│  └─ 8. 公平锁 / 非公平锁
├─ 七、线程池与任务调度
│  ├─ 1. Executor
│  ├─ 2. ExecutorService
│  ├─ 3. ThreadPoolExecutor
│  ├─ 4. submit()
│  ├─ 5. execute()
│  ├─ 6. 拒绝策略
│  └─ 7. 为什么不建议 Executors 默认工厂直接无脑用
└─ 八、并发集合与工具
   ├─ 1. ConcurrentHashMap
   ├─ 2. CopyOnWriteArrayList
   ├─ 3. BlockingQueue
   ├─ 4. CountDownLatch
   ├─ 5. CyclicBarrier
   ├─ 6. Semaphore
   └─ 7. AtomicInteger
```

## 4. 面试角度最常考的主线

线程这章在面试里，通常不是按工具名一个一个问，而是按主线追问：

### 4.1 第一条主线：线程怎么创建和运行

常见问题：

- 创建线程有几种方式？
- `run()` 和 `start()` 区别是什么？
- `Runnable` 和 `Callable` 区别是什么？

### 4.2 第二条主线：线程为什么不安全

常见问题：

- 什么是线程安全？
- 为什么会有线程安全问题？
- `volatile` 为什么不能保证复合操作安全？

### 4.3 第三条主线：Java 怎么解决线程安全问题

常见问题：

- `synchronized` 怎么理解？
- `synchronized` 和 `Lock` 区别是什么？
- `volatile` 适合什么场景？

### 4.4 第四条主线：实际开发怎么管理线程

常见问题：

- 为什么更推荐线程池？
- 线程池核心参数有哪些？
- 为什么 `ConcurrentHashMap` 比 `Hashtable` 更常用？

## 5. 当前阶段最该先补的文档

如果按面试准备来推进，建议这一章优先补：

1. 线程创建方式
2. 线程状态与常见方法
3. `sleep` / `wait` / `notify` / `join`
4. `synchronized`
5. `volatile`
6. 线程池
7. 并发高频面试题

## 6. 一句话总结

线程与并发这章的族谱，核心不是记住多少工具，而是先把“线程基础 -> 并发问题 -> 同步手段 -> 线程池与并发工具”这条主线装进脑子里。
