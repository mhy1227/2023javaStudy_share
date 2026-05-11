# 线程外部高频补充记录

## 1. 这一份是干什么的

这一份不是正式问答稿，而是根据牛客、LeetCode 中文社区里线程/并发相关面经与讨论，先做一份：

- 高频点记录
- 场景题记录
- 后续可继续补文档的线索记录

写这份的目的很简单：

- 先把外部重复出现的点固定下来
- 后面再按这些点拆成“问题版”和“口语化标答版”

## 2. 本次记录的时间与范围

记录时间：

- 2026-04-20

主要参考范围：

- 牛客面经/技术讨论
- LeetCode 中文讨论区

重点看的是：

- 线程池
- `ThreadLocal`
- `CompletableFuture`
- 定时任务线程池
- `ForkJoinPool`
- 多线程手撕题/同步题

## 3. 外部重复出现的高频点

结合这轮检索，重复出现比较多的线程高频点主要还是下面这些：

1. 线程池 7 个核心参数
2. 线程池执行流程
3. 阻塞队列和拒绝策略
4. 线程池大小如何设置
5. `ThreadLocal` 的作用、内存泄漏、在线程池里为什么要 `remove()`
6. `CompletableFuture` 的异步编排、默认线程池、异常处理
7. `ScheduledThreadPool` 和 `Timer` 的区别
8. `ForkJoinPool` / `commonPool`
9. 线程排障场景题
10. 多线程同步手撕题

## 4. 已经在当前笔记里覆盖得比较多的

你现在仓库里，下面这些已经补得相对比较完整了：

### 4.1 线程池基础

已覆盖：

- 参数
- 类型
- 建池思路
- 实战配置
- 面试题和 checklist

对应文档可回看：

- [thread-pool-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/010-Thread/thread-pool-note.md)
- [thread-pool-practice-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/010-Thread/practical-topics/thread-pool-practice-note.md)
- [thread-pool-parameters-and-types-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/010-Thread/practical-topics/thread-pool-parameters-and-types-note.md)
- [thread-pool-design-and-selection-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/010-Thread/practical-topics/thread-pool-design-and-selection-note.md)

### 4.2 `CompletableFuture`

已覆盖：

- 基础用途
- 常见方法
- 面试里怎么讲

可回看：

- [completablefuture-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/010-Thread/practical-topics/completablefuture-note.md)

### 4.3 线程排障

已覆盖：

- CPU 飙高
- 死锁
- 线程池打满
- 线程阻塞

可回看：

- [thread-troubleshooting-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/010-Thread/practical-topics/thread-troubleshooting-note.md)

## 5. 结合外部来源，当前最值得继续补的

如果继续往下补，最自然的优先级建议如下。

### 5.1 第一优先级：`ThreadLocal`

原因：

- 牛客和 LeetCode 中文区里，`ThreadLocal` 仍然非常常见
- 尤其是“为什么会内存泄漏”“线程池里为什么要 `remove()`”这两个点

最值得补的子点：

1. `ThreadLocal` 是干什么的
2. `ThreadLocalMap` 粗理解
3. key 为什么是弱引用
4. value 为什么可能残留
5. 为什么在线程池环境更要及时 `remove()`
6. `InheritableThreadLocal` 和 `TransmittableThreadLocal` 是什么

### 5.2 第二优先级：`ScheduledThreadPool` / `Timer`

原因：

- 牛客的线程池高频整理里，会带到定时线程池
- 面试里容易顺手追到“为什么不用 `Timer`”

最值得补的子点：

1. `ScheduledThreadPool` 适合什么场景
2. 延迟任务和周期任务
3. 和 `Timer` 的区别
4. 底层为什么会提到 `DelayedWorkQueue` / `DelayQueue`

### 5.3 第三优先级：`ForkJoinPool`

原因：

- 不一定是绝对高频，但已经是明显的加分项
- `CompletableFuture` 默认线程池也很容易顺带追到它

最值得补的子点：

1. `ForkJoinPool` 是干什么的
2. 适合什么任务
3. work-stealing 的粗理解
4. `commonPool` 是什么
5. 为什么不适合拿去跑长时间阻塞任务

### 5.4 第四优先级：线程池监控与动态调优

原因：

- 这块在面经里不如前面三块高频
- 但在项目面试里很像“真实经验加分题”

最值得补的子点：

1. 常看哪些监控指标
2. 任务堆积怎么判断
3. 活跃线程长期打满说明什么
4. 是否需要动态调参

## 6. 外部来源里反复出现的场景题

这类题很值得后面单独补成“场景题文档”。

### 6.1 线程池打满怎么办

高频原因：

- 这是最典型的项目场景题

常见追问：

- 你先看哪些指标
- 是线程池太小，还是任务太慢，还是下游卡住

### 6.2 为什么核心业务和非核心业务要线程池隔离

常见追问：

- 如果共用一个线程池会怎样
- 资源被谁抢走了

### 6.3 为什么在线程池里用 `ThreadLocal` 要格外注意

常见追问：

- 线程复用会带来什么问题
- 为什么请求 A 的数据可能污染到请求 B

### 6.4 多个 RPC / 多个查询并行后再汇总怎么做

常见追问：

- 你会不会考虑 `CompletableFuture`
- 哪一步做超时控制
- 哪一步做异常兜底

### 6.5 定时任务为什么更常用 `ScheduledThreadPool`

常见追问：

- 和 `Timer` 相比好在哪
- 底层队列为什么适合做延时调度

### 6.6 100 个任务分 10 批并发执行，但批次之间有顺序

这一类在 LeetCode 中文区属于比较典型的场景题。

它考的不是某一个 API，而是：

- 线程池
- `CountDownLatch`
- `CyclicBarrier`
- 批次控制
- 主线程汇总

## 7. LeetCode 这边更偏什么

LeetCode 中文区更偏：

- 多线程同步题
- 手撕协作题
- 场景化并发控制题

典型模型包括：

1. 按序打印
2. 交替打印
3. FizzBuzz 多线程版
4. 有界阻塞队列
5. 哲学家进餐
6. 分批并发执行

如果继续补练习区，这些模型都值得继续纳入。

## 8. 当前最自然的后续补文档建议

如果按“先高频、再加分、再扩场景”的顺序补，建议是：

1. `threadlocal-note.md`
2. `scheduled-thread-pool-note.md`
3. `forkjoinpool-note.md`
4. `thread-pool-monitoring-and-tuning-note.md`
5. `thread-scenario-questions.md`

## 9. 外部参考链接

### 9.1 牛客

- Java 面试：`ThreadLocal` 学会了这些，你也能和面试官扯皮了！  
  https://www.nowcoder.com/discuss/353149174386466816

- 面试必备之深入理解 `thread local`  
  https://www.nowcoder.com/discuss/752094391308652544

- 一文搞懂 `ThreadLocal`，是时候反问面试官了  
  https://www.nowcoder.com/discuss/514704377869885440

- Java 后端高频面试问题：线程池  
  https://www.nowcoder.com/discuss/820704

- 一篇搞定 Java 线程池面试点  
  https://www.nowcoder.com/discuss/152050

- 线程池  
  https://www.nowcoder.com/discuss/353147349147000832

- Java 中的 Fork/Join 框架  
  https://www.nowcoder.com/discuss/731100303457538048

- java 并发八股  
  https://www.nowcoder.com/discuss/723179322629980160

### 9.2 LeetCode 中文区

- 线程池面试必备整理  
  https://leetcode.cn/circle/discuss/XYOO57/

- `ThreadLocal` 面试题汇总  
  https://leetcode.cn/discuss/post/3162760/ba-gu-qu-shi-javaduo-xian-cheng-threadlo-xcss/

- 并发 + 项目相关复习准备  
  https://leetcode.cn/discuss/post/3101323/bing-fa-xiang-mu-xiang-guan-fu-xi-zhun-bei

- 多线程计数及 LeetCode 多线程同步问题详解  
  https://leetcode.cn/circle/discuss/QIS8Qv/

- Java 多线程：100 个任务分 10 批执行，每批有顺序  
  https://leetcode.cn/discuss/post/3572005/javaduo-xian-cheng-you-100ge-ren-wu-xu-y-f6bp/

## 10. 一句话总结

这轮外部检索后，线程这一章如果继续补，最值得优先做的不是再重复基础定义，而是：

- `ThreadLocal`
- 定时线程池
- `ForkJoinPool`
- 线程池监控与调优
- 场景题整理
