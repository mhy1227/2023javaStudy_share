# 并发底层机制 Checklist

## 1. 这一份怎么用

这一份不是知识点详解，而是 `core-mechanisms` 这一层的最终复盘清单。

适合用法：

- 学完整个子目录后做自查
- 面试前最后快速过一遍
- 找出自己还答不顺的点

你可以把每一条都当成一个问题去问自己：

- 我能不能用自己的话讲清楚？
- 我能不能举一个简单场景？
- 我能不能区分相近概念？

## 2. CAS Checklist

- 我能讲清楚什么是 CAS
- 我能讲清楚 CAS 的核心是“比较并更新”
- 我知道 CAS 更偏乐观锁思路
- 我能讲清楚为什么 `AtomicInteger` 和 CAS 会连着讲
- 我知道 CAS 失败后可能会重试
- 我知道 CAS 重试会带来自旋开销
- 我知道 CAS 不是所有并发问题都能解决
- 我能讲清楚 ABA 问题的大致含义
- 我知道 `AtomicStampedReference` 常用来处理 ABA
- 我能讲清楚 CAS 适合简单单变量原子更新

## 3. 自旋 Checklist

- 我能讲清楚什么是自旋
- 我知道自旋是“先不阻塞，短时间反复尝试”
- 我能讲清楚自旋和阻塞的区别
- 我知道自旋本质上是拿 CPU 换线程切换成本
- 我知道自旋适合短等待、短临界区
- 我知道自旋不适合长时间空转
- 我知道竞争太激烈时自旋可能反而更差
- 我能把自旋和 CAS 的关系串起来

## 4. AQS Checklist

- 我知道 AQS 的全称是 `AbstractQueuedSynchronizer`
- 我能讲清楚 AQS 是什么
- 我能讲清楚为什么需要 AQS
- 我知道 AQS 可以粗理解成“状态 + 等待队列”
- 我知道 `ReentrantLock` 常和 AQS 连着讲
- 我知道 `CountDownLatch`、`Semaphore` 这类工具也常和 AQS 有关
- 我知道当前阶段先建立整体认知，不必死抠全部源码
- 我能讲清楚 AQS 和 `synchronized` 不是同一条实现路线

## 5. park / unpark Checklist

- 我知道 `park()` 是让线程停下来等
- 我知道 `unpark()` 是给线程继续执行的许可
- 我知道它们常通过 `LockSupport` 使用
- 我能讲清楚 `park/unpark` 和 `wait/notify` 的区别
- 我知道 `wait/notify` 基于对象监视器
- 我知道 `park/unpark` 不强依赖对象锁
- 我知道 `unpark` 可以先于 `park`
- 我能讲清楚它和 AQS、线程阻塞唤醒的关系

## 6. LongAdder Checklist

- 我知道 `LongAdder` 适合高并发累加统计
- 我能讲清楚为什么高并发计数常提 `LongAdder`
- 我能讲清楚它和 `AtomicLong` 的区别
- 我知道它的核心思路是分散单点竞争
- 我知道它常见场景是访问量、请求数、监控指标统计
- 我知道 `LongAdder` 不是所有原子更新场景都要优先使用

## 7. 原子类 Checklist

- 我能讲清楚什么是原子类
- 我知道为什么有了锁还需要原子类
- 我知道原子类更适合简单共享变量更新
- 我知道原子类和 CAS 关系很紧
- 我知道 `AtomicInteger` / `AtomicLong` 适合简单计数
- 我知道 `AtomicBoolean` 适合标志位和开关位
- 我知道 `AtomicReference` 适合原子替换对象引用
- 我知道 `AtomicStampedReference` 适合配合版本处理 ABA
- 我能讲清楚 `AtomicLong` 和 `LongAdder` 怎么选
- 我知道单个原子操作线程安全，不等于整个业务流程线程安全

## 8. 串联理解 Checklist

- 我能把 CAS、自旋、AQS、`park/unpark` 串成一条主线
- 我能讲清楚原子类为什么会和 CAS 连起来
- 我能讲清楚为什么高并发计数会从原子类追到 `LongAdder`
- 我能讲清楚为什么 AQS、`LockSupport`、显式锁会经常一起出现
- 我能讲清楚这些机制不是孤立概念，而是在共同支撑 JUC 并发体系

## 9. 面试表达 Checklist

- 我回答时不会只背类名
- 我回答时会先给结论，再补关键词，再补场景
- 我不会把单变量原子更新误说成整个业务都线程安全
- 我不会把 `LongAdder` 说成一定全面优于 `AtomicLong`
- 我不会把 AQS 回答成单纯“一个类名”
- 我能把“适合什么场景、不适合什么场景”主动补出来

## 10. 最后自测

如果下面这些问题你都能顺着答下来，说明这一层已经比较稳了：

- 什么是 CAS？它有什么问题？
- 什么是 ABA？怎么处理？
- 什么是自旋？它和阻塞有什么区别？
- AQS 是什么？为什么需要它？
- `park/unpark` 和 `wait/notify` 怎么区分？
- 为什么高并发计数常用 `LongAdder`？
- 原子类和锁是什么关系？
- `AtomicReference` 和 `AtomicStampedReference` 分别解决什么问题？

