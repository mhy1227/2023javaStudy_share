# 高并发与中间件补充

## 1. 这一目录放什么

这一目录主要承接 `010-Thread` 之后，再往上一层走的知识点。

也就是说，这里不再只是讲：

- 单机线程
- 锁
- 线程池

而是开始讲：

- 流量治理
- 中间件缓冲
- 分布式协作
- 高并发架构思路
- JVM 对并发的影响

## 2. 为什么要单独开新目录

因为下面这些知识点虽然和线程强相关，但已经不适合再混在线程目录里：

1. 消息队列里的异步削峰
2. 分布式锁
3. 高并发系统设计
4. Netty / NIO 更深层并发模型
5. JVM 层面对并发的影响

它们更像：

- 线程之后的下一层

## 3. 当前目录索引

- [mq-async-peak-shaving-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/mq-async-peak-shaving-note.md)
- [distributed-lock-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-lock-note.md)
- [distributed-id-snowflake-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-id-snowflake-note.md)
- [distributed-id-solution-comparison-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-id-solution-comparison-note.md)
- [sharding-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/sharding-note.md)
- [sharding-transaction-consistency-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/sharding-transaction-consistency-note.md)
- [distributed-infrastructure-scene-questions.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-infrastructure-scene-questions.md)
- [distributed-infrastructure-high-frequency-questions.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-infrastructure-high-frequency-questions.md)
- [distributed-infrastructure-1min-3min-answer-pack.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-infrastructure-1min-3min-answer-pack.md)
- [distributed-infrastructure-mock-oral-script.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-infrastructure-mock-oral-script.md)
- [distributed-infrastructure-final-checklist.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-infrastructure-final-checklist.md)
- [distributed-infrastructure-last-minutes.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/distributed-infrastructure-last-minutes.md)
- [database-sharding-questions/README.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/database-sharding-questions/README.md)
- [database-sharding-questions/cross-shard-join-and-non-sharding-key-query-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/database-sharding-questions/cross-shard-join-and-non-sharding-key-query-note.md)
- [database-sharding-questions/hot-shard-and-hotspot-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/database-sharding-questions/hot-shard-and-hotspot-note.md)
- [database-sharding-questions/rebalance-and-migration-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/database-sharding-questions/rebalance-and-migration-note.md)
- [database-sharding-questions/sharding-key-selection-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/database-sharding-questions/sharding-key-selection-note.md)
- [database-sharding-questions/horizontal-vs-vertical-sharding-answer-pack.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/database-sharding-questions/horizontal-vs-vertical-sharding-answer-pack.md)
- [high-concurrency-system-design-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/high-concurrency-system-design-note.md)
- [netty-nio-concurrency-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/netty-nio-concurrency-note.md)
- [jvm-concurrency-impact-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/011-HighConcurrency-Middleware/jvm-concurrency-impact-note.md)

## 4. 一句话总结

这一目录不是再背线程 API，而是补“线程之外，高并发系统还要怎么设计和治理”，目前也已经开始延伸到分布式 ID 这类基础设施话题。
