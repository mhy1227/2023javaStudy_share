# 并发底层机制高频面试题

## 1. 这一份怎么用

这一份不是详细答案版，而是把 `core-mechanisms` 这一层最值得反复背的问题集中列出来。

适合用法：

- 面试前最后过题
- 模拟面试时抽问自己
- 配合口语版问答一起复习

建议答题顺序：

- 先说结论
- 再补关键词
- 最后补一个场景或边界

## 2. CAS 高频题

- 什么是 CAS？
- CAS 为什么会和原子类连着讲？
- CAS 为什么不一定要加锁？
- CAS 有什么优点？
- CAS 有什么局限？
- 什么是 ABA 问题？
- ABA 为什么会出现？
- ABA 一般怎么处理？
- `AtomicInteger` 为什么线程安全？
- CAS 适合什么场景？不适合什么场景？

## 3. 自旋 高频题

- 什么是自旋？
- 自旋和阻塞有什么区别？
- 为什么有的并发更新不立刻阻塞线程？
- 自旋为什么有时更快？
- 自旋为什么也可能更浪费 CPU？
- 什么场景适合自旋？
- 什么场景不适合自旋？
- CAS 和自旋是什么关系？

## 4. AQS 高频题

- 什么是 AQS？
- AQS 的全称是什么？
- 为什么需要 AQS？
- AQS 解决了什么共性问题？
- 怎么理解 AQS 的“状态 + 等待队列”？
- `ReentrantLock` 和 AQS 是什么关系？
- `Semaphore`、`CountDownLatch` 为什么也会提到 AQS？
- AQS 和 `synchronized` 有什么区别？
- AQS 当前阶段需要了解到什么程度？

## 5. park / unpark 高频题

- 什么是 `park/unpark`？
- 为什么并发包里经常提 `LockSupport`？
- `park/unpark` 和 `wait/notify` 有什么区别？
- 为什么说 `unpark` 可以先于 `park`？
- `park/unpark` 和线程阻塞唤醒是什么关系？
- `park/unpark` 和 AQS 为什么经常连着讲？

## 6. LongAdder 高频题

- 什么是 `LongAdder`？
- 为什么高并发计数常提 `LongAdder`？
- `LongAdder` 解决的核心问题是什么？
- `LongAdder` 和 `AtomicLong` 怎么选？
- `LongAdder` 适合什么场景？
- `LongAdder` 不适合什么场景？

## 7. 原子类 高频题

- 什么是原子类？
- 为什么有了锁还需要原子类？
- 原子类和锁是什么关系？
- 原子类底层为什么能线程安全？
- 常见原子类有哪些？
- `AtomicInteger` 适合什么场景？
- `AtomicBoolean` 常用来做什么？
- `AtomicReference` 是干什么的？
- `AtomicStampedReference` 是干什么的？
- `AtomicLong` 和 `LongAdder` 怎么选？
- 单个原子操作线程安全，为什么整个业务流程仍可能不安全？

## 8. 串联追问题

- CAS、自旋、AQS、`park/unpark` 之间是什么关系？
- 为什么原子类会追到 CAS？
- 为什么显式锁和 AQS 会追到 `LockSupport`？
- 为什么高并发统计会从 `AtomicLong` 继续追到 `LongAdder`？
- 这些底层机制共同支撑了 Java 并发体系的哪些部分？

## 9. 容易答偏的题

- 你不要把 CAS 说成“绝对无成本”
- 你不要把原子类说成“完全替代锁”
- 你不要把 `LongAdder` 说成“全面优于 `AtomicLong`”
- 你不要把 AQS 只答成一个类名
- 你不要把 `park/unpark` 和 `wait/notify` 混成一套东西
- 你不要把“单操作原子”误答成“整个流程都线程安全”

## 10. 最后一轮高频自测题

- 什么是 CAS？为什么它更偏乐观锁？
- 什么是 ABA？`AtomicStampedReference` 怎么解决它？
- 自旋和阻塞的核心差异是什么？
- AQS 为什么重要？它解决了什么问题？
- `park/unpark` 和 `wait/notify` 最关键的区别是什么？
- 为什么 `LongAdder` 在高并发计数里更常被提到？
- 原子类和锁怎么选？
- 为什么说单变量原子更新不等于复合业务线程安全？

