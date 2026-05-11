# 线程牛客高频面试题

## 1. 这一份是做什么的

这一份单独只放问题，不展开答案。

适合用法：

- 快速过题
- 自测能不能口述出来
- 面试前最后一轮扫题

如果你想同时看标答，可以配合本目录下另一份：

- `thread-nowcoder-high-frequency-answers.md`

## 2. 牛客里线程这块高频主要集中在哪

牛客上的 Java 面经里，线程 / 并发这块高频通常比较集中，主要就是这几条主线：

1. 进程、线程、多线程、并发、并行
2. 创建线程与线程状态
3. `sleep()`、`wait()`、`notify()`、`join()`
4. 线程安全、原子性、可见性、有序性
5. `synchronized`、`volatile`、`Lock`
6. 线程池
7. `ConcurrentHashMap`、`CopyOnWriteArrayList`、`BlockingQueue`
8. 少量并发工具类，例如 `CountDownLatch`、`CyclicBarrier`

## 3. 第一梯队：最常被直接问

1. 进程和线程有什么区别？
2. 什么是并发？什么是并行？
3. 创建线程有哪几种方式？
4. `run()` 和 `start()` 有什么区别？
5. 线程有哪些状态？
6. `sleep()` 和 `wait()` 有什么区别？
7. 什么是线程安全？
8. 什么是原子性、可见性、有序性？
9. 什么是 `synchronized`？
10. 什么是 `volatile`？
11. 为什么 `volatile` 不能保证 `i++` 线程安全？
12. 为什么一般更推荐使用线程池？

## 4. 第二梯队：很容易连着追问

1. `wait()` 为什么必须在同步代码块里使用？
2. `notify()` 和 `notifyAll()` 有什么区别？
3. `sleep()` 会不会释放锁？
4. `wait()` 会不会释放锁？
5. `synchronized` 锁的是什么？
6. 同步实例方法、同步静态方法、同步代码块分别锁什么？
7. `synchronized` 和 `volatile` 有什么区别？
8. `Lock` 和 `synchronized` 有什么区别？
9. 什么是可重入？
10. 为什么 `unlock()` 一般要放在 `finally` 里？

## 5. 第三梯队：线程池高频题

1. 为什么不推荐频繁 `new Thread()`？
2. 什么是线程池？
3. `execute()` 和 `submit()` 有什么区别？
4. `ThreadPoolExecutor` 核心参数有哪些？
5. 线程池处理任务的大致流程是什么？
6. 常见拒绝策略有哪些？
7. 为什么不建议无脑使用 `Executors` 默认工厂？

## 6. 第四梯队：并发容器高频题

1. 为什么普通集合在并发环境下容易出问题？
2. `ConcurrentHashMap` 为什么比 `Hashtable` 更常用？
3. `CopyOnWriteArrayList` 适合什么场景？
4. `BlockingQueue` 有什么用？
5. 并发容器是不是就能解决所有并发问题？

## 7. 第五梯队：常见延伸题

1. 什么是死锁？怎么避免？
2. 什么是上下文切换？
3. 什么是 `ThreadLocal`？
4. `CountDownLatch` 和 `CyclicBarrier` 有什么区别？
5. 项目里线程池一般怎么用？
6. 项目里并发容器一般怎么用？

## 8. 一轮复习优先级

如果时间不够，优先口述这几题：

1. 进程和线程的区别
2. 创建线程有哪几种方式
3. `run()` 和 `start()` 的区别
4. `sleep()` 和 `wait()` 的区别
5. 什么是线程安全
6. `synchronized` 锁的是什么
7. `volatile` 为什么不能保证 `i++`
8. 为什么要用线程池
9. 线程池核心参数有哪些
10. `ConcurrentHashMap` 为什么更常用

## 9. 外部参考

- 牛客：Java 八股大纲，很全！！  
  https://www.nowcoder.com/discuss/835134193616109568
- 牛客：2024春招八股文  
  https://www.nowcoder.com/discuss/606865026484289536
- 牛客：牛客题霸 Java篇  
  https://www.nowcoder.com/discuss/719427031755718656
- 牛客：暑期实习八股整理  
  https://www.nowcoder.com/discuss/649670711828430848
