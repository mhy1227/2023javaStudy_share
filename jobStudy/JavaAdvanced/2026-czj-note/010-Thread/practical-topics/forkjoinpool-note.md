# `ForkJoinPool` 补充笔记

## 1. 为什么这一份要单独补

`ForkJoinPool` 不一定像线程池 7 个参数那样必问，但在并发面试里属于明显的加分点。

它经常会从两个方向被追问出来：

- 分治任务怎么并行处理
- `CompletableFuture` 默认线程池是什么

所以这一份主要补：

- `ForkJoinPool` 是干什么的
- 它适合什么任务
- 为什么会提到 work-stealing
- 它和 `CompletableFuture` 有什么关系

## 2. 先一句话理解 `ForkJoinPool`

可以先记一个口径：

- `ForkJoinPool` 是一种适合处理可拆分任务的线程池，核心思路是把大任务拆成小任务并行执行，最后再把结果合并

也就是两个关键词：

- fork：拆分任务
- join：合并结果

## 3. 它适合什么任务

最适合的是：

- 可以递归拆分
- 子任务之间相对独立
- 最后可以汇总结果

典型例子：

1. 大数组求和
2. 批量数据处理
3. 分治算法
4. 并行计算类任务

不太适合的是：

- 长时间阻塞 IO
- 大量等待数据库/RPC 的任务

因为 `ForkJoinPool` 更适合 CPU 计算类的拆分合并，不是专门拿来堆阻塞任务的。

## 4. `ForkJoinPool` 和普通线程池有什么区别

普通线程池更常见的模型是：

- 任务提交到公共队列
- 工作线程从队列里拿任务执行

`ForkJoinPool` 更强调：

- 任务可以继续拆分出子任务
- 每个工作线程通常有自己的任务队列
- 工作线程之间可以发生任务窃取

这就是它和普通 `ThreadPoolExecutor` 的一个重要差异。

## 5. 什么是 work-stealing

work-stealing 通常翻译成：

- 工作窃取

粗理解就够了：

- 某个线程自己的任务做完了，不是闲着，而是去其他线程的任务队列里偷一些任务来执行

这样可以尽量减少线程空闲，提高整体并行效率。

面试里可以这样说：

- work-stealing 的目的，是让空闲线程主动去帮忙处理其他队列里的任务，提高任务拆分后的执行效率

## 6. `RecursiveTask` 和 `RecursiveAction`

当前阶段先记两个类：

1. `RecursiveTask`
2. `RecursiveAction`

### 6.1 `RecursiveTask`

- 有返回值的 fork/join 任务

比如：

- 并行计算一个数组的和

### 6.2 `RecursiveAction`

- 没有返回值的 fork/join 任务

比如：

- 并行处理一批数据，不关心返回值

## 7. 一个粗略的数组求和思路

不用一上来背完整代码，先理解思路：

1. 如果数组范围足够小，直接求和
2. 如果范围太大，拆成左右两半
3. 左右两半分别计算
4. 最后合并两个结果

这就是很典型的：

- fork
- join

## 8. `commonPool` 是什么

`ForkJoinPool` 里有一个常见概念：

- `commonPool`

可以先粗理解成：

- JDK 提供的一个公共 `ForkJoinPool`

它很容易和 `CompletableFuture` 一起被问到。

因为很多 `CompletableFuture` 的异步方法，如果不显式传入线程池，默认可能会使用公共线程池。

## 9. 为什么不建议所有异步任务都依赖默认 `commonPool`

原因很简单：

- 公共线程池是共享资源

如果你把很多业务异步任务都丢给默认公共池，可能会出现：

1. 不同业务互相影响
2. 阻塞任务拖慢公共池
3. 排障时不容易区分任务来源
4. 线程池参数不够业务可控

所以实际项目里，很多时候更推荐：

- 给 `CompletableFuture` 显式传入自定义线程池

## 10. `ForkJoinPool` 为什么不适合长时间阻塞任务

因为它的优势主要在：

- 拆分计算
- 并行执行
- 工作窃取

如果大量任务都在等数据库、网络、RPC，就会让工作线程长时间被占住。

这时它的优势发挥不出来，还可能影响其他使用同一个池的任务。

所以面试里可以说：

- `ForkJoinPool` 更适合计算型分治任务，不太适合大量长时间阻塞任务

## 11. 面试里怎么回答“`ForkJoinPool` 是什么”

可以直接背一版：

`ForkJoinPool` 是 Java 里适合处理分治任务的一种线程池，它会把大任务拆成小任务并行执行，最后再把结果合并。它里面有 work-stealing 的思想，空闲线程可以去其他线程的队列里窃取任务执行，提高并行效率。

## 12. 面试里怎么回答“它和 `CompletableFuture` 有什么关系”

可以直接背一版：

`CompletableFuture` 的一些异步方法如果不显式指定线程池，默认可能会使用公共的 `ForkJoinPool.commonPool()`。所以实际项目里，如果异步任务比较重要或者可能阻塞，我一般更倾向传入自定义线程池，避免不同业务互相影响。

## 13. 面试里怎么回答“为什么不适合阻塞任务”

可以直接背一版：

`ForkJoinPool` 更适合 CPU 计算型、可拆分合并的任务。如果任务大量阻塞在 IO、数据库或者 RPC 上，工作线程会长时间被占用，work-stealing 的优势发挥不出来，还可能拖慢公共线程池里的其他任务。

## 14. 当前阶段最值得记什么

这一份最少要记住：

1. `ForkJoinPool` 适合分治任务
2. `fork` 是拆分，`join` 是合并
3. work-stealing 是空闲线程去偷任务做
4. `RecursiveTask` 有返回值，`RecursiveAction` 无返回值
5. `CompletableFuture` 默认可能用 `commonPool`
6. 项目里重要异步任务更推荐显式传自定义线程池

## 15. 一句话总结

`ForkJoinPool` 这块不用一开始背源码，先把三件事讲顺：

- 适合什么任务
- work-stealing 是什么
- 为什么和 `CompletableFuture.commonPool()` 有关系
