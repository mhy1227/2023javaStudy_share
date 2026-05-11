# CompletableFuture 补充笔记

## 1. 为什么这一份要单独补

线程池和 `Callable` 讲完以后，实际开发里很容易继续追到：

- 异步任务怎么编排
- 多个任务怎么串起来
- 一个任务结果怎么继续传给下一个

这时就很容易碰到：

- `CompletableFuture`

所以这一份主要补：

- `CompletableFuture` 到底是干什么的
- 当前阶段该掌握到什么程度

## 2. 先一句话理解 `CompletableFuture`

可以先记一个口径：

- `CompletableFuture` 是 Java 里非常常见的一种异步编排工具

更直白一点说：

- 它不只是“开异步”
- 更重要的是“把异步任务继续串起来”

## 3. 为什么它会比 `Future` 更常被追问

因为传统 `Future` 更像：

- 提交一个任务
- 后面拿结果

但如果你想继续做：

- 任务 A 完成后继续做任务 B
- 两个任务并行后再汇总
- 异常统一处理

那 `CompletableFuture` 会更自然。

## 4. 当前阶段最值得先记哪些方法

如果你现在不想学太散，可以先优先记：

1. `runAsync`
2. `supplyAsync`
3. `thenApply`
4. `thenAccept`
5. `thenRun`
6. `thenCombine`
7. `allOf`
8. `exceptionally`

这几组已经够搭一个基础异步编排认知框架。

## 5. `runAsync` 和 `supplyAsync` 怎么粗分

可以先记成：

- `runAsync` 更像异步执行一个没有返回值的任务
- `supplyAsync` 更像异步执行一个有返回值的任务

这一组非常高频。

## 6. `thenApply` / `thenAccept` / `thenRun` 怎么粗分

这是 `CompletableFuture` 最容易混的一组。

可以先记一个很实用的口径：

- `thenApply`：接前一个结果，再加工，自己也有返回值
- `thenAccept`：接前一个结果，消费掉，不返回值
- `thenRun`：不关心前一个结果，只是接着跑下一个动作

只要这组能答顺，基础面试就已经比较够用了。

## 7. `allOf` 和组合任务怎么理解

如果面试官继续问：

- 多个异步任务怎么一起等？

你就应该想到：

- `allOf`

它可以先粗理解成：

- 等多个任务都完成

这类题很适合讲：

- 并行任务汇总

## 8. 为什么 `CompletableFuture` 经常和线程池一起讲

因为异步任务最终还是要落到线程上跑。

所以你最好有一个认知：

- `CompletableFuture` 是异步编排工具
- 线程池是底层执行资源

也就是说，这两者不是替代关系，而是：

- 经常配合出现

## 9. 异常处理为什么也是高频点

因为异步任务一多，异常处理就很容易被忽略。

所以面试里很容易追：

- 异步任务出错了怎么办？

这时你至少要先能想到：

- `exceptionally`

如果能讲到：

- 异常不能完全靠外层 `try-catch`

层次会更好一些。

## 10. 面试里怎么回答“什么是 `CompletableFuture`”

可以直接背一版：

`CompletableFuture` 可以理解成 Java 里非常常见的一种异步编排工具。它不只是把任务异步执行出去，更重要的是可以把后续任务继续串起来，比如前一个结果继续加工、多个任务并行后再汇总，以及统一处理异常。所以它比传统 `Future` 更适合写复杂一点的异步流程。

## 11. 面试里怎么回答“为什么它经常和线程池一起讲”

可以背一版短的：

因为 `CompletableFuture` 更像异步任务的编排工具，而线程池更像这些异步任务的执行资源。一个负责“怎么组织异步流程”，一个负责“线程怎么跑任务”，所以实际开发里这两者经常配合使用。

## 12. 当前阶段记忆重点

这一份最少要记住：

1. `CompletableFuture` 是异步编排工具
2. 它比传统 `Future` 更适合串联任务
3. `runAsync` / `supplyAsync` 是入口高频方法
4. `thenApply` / `thenAccept` / `thenRun` 要能粗分
5. `allOf` 常用于并行任务汇总
6. `exceptionally` 常和异常处理一起讲
7. 它经常和线程池配合出现

