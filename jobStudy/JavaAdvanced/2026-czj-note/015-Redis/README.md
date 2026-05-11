# 015-Redis

## 1. 这一章是干什么的

这一章专门整理 Redis 在 Java 后端面试里的主干知识。

它不是只背命令，而是重点整理：

- Redis 是什么
- 为什么快
- 常见数据结构怎么选
- 持久化怎么理解
- 缓存穿透、击穿、雪崩怎么答
- 分布式锁怎么讲

Redis 这一章和前面的很多内容都能串起来：

- 和 `012-MySQL` 串缓存一致性
- 和 `010-Thread`、`011-HighConcurrency-Middleware` 串高并发和锁
- 和后面的 MQ、分布式系统串削峰、解耦、最终一致性

## 2. 为什么值得单独开目录

因为 Redis 在面试里特别高频，而且很少单独问命令，更多是这样问：

- Redis 为什么快
- 你项目里 Redis 怎么用
- 缓存和数据库怎么保持一致
- 热点 key 怎么处理
- 分布式锁怎么实现
- Redis 持久化怎么选

所以这章要按“项目 + 原理 + 高频问法”来整理。

## 3. 当前目录结构

- `redis-basic-overview.md`
- `redis-data-structure-note.md`
- `redis-pipeline-transaction-lua-note.md`
- `redis-persistence-note.md`
- `redis-cache-problem-note.md`
- `redis-distributed-lock-note.md`
- `redis-expire-eviction-note.md`
- `redis-high-availability-note.md`
- `redis-master-slave-replication-advanced.md`
- `redis-sentinel-cluster-deep-dive.md`
- `redis-hotkey-bigkey-note.md`
- `redis-distributed-lock-advanced.md`
- `redis-cache-consistency-advanced.md`
- `redis-special-structures-and-scenes.md`
- `comparison/`
- `high-frequency-and-mock/`

## 4. 怎么看最顺

建议顺序：

1. `redis-basic-overview.md`
2. `redis-data-structure-note.md`
3. `redis-pipeline-transaction-lua-note.md`
4. `redis-persistence-note.md`
5. `redis-cache-problem-note.md`
6. `redis-distributed-lock-note.md`
7. `redis-expire-eviction-note.md`
8. `redis-high-availability-note.md`
9. `redis-master-slave-replication-advanced.md`
10. `redis-sentinel-cluster-deep-dive.md`
11. `redis-hotkey-bigkey-note.md`
12. `redis-distributed-lock-advanced.md`
13. `redis-cache-consistency-advanced.md`
14. `redis-special-structures-and-scenes.md`
15. `comparison/redis-compare-note.md`
16. `comparison/redis-cache-problem-compare-note.md`
17. `high-frequency-and-mock/redis-high-frequency-qa.md`
18. `high-frequency-and-mock/redis-project-scene-questions.md`
19. `high-frequency-and-mock/redis-mock-chain-questions.md`
20. `high-frequency-and-mock/nowcoder-real-interview/redis-nowcoder-high-frequency.md`
21. `high-frequency-and-mock/nowcoder-real-interview/redis-nowcoder-answer-pack.md`
22. `high-frequency-and-mock/nowcoder-real-interview/redis-nowcoder-mock-questions.md`
23. `high-frequency-and-mock/nowcoder-real-interview/redis-nowcoder-last-10-minutes.md`
24. `high-frequency-and-mock/redis-one-page-cheatsheet.md`
25. `high-frequency-and-mock/redis-real-interview-trap-questions.md`
26. `high-frequency-and-mock/redis-project-oral-pack-advanced.md`
27. `high-frequency-and-mock/redis-final-checklist.md`
28. `high-frequency-and-mock/redis-mock-oral-script.md`

## 5. 一句话记住

> Redis 这一章不是背命令大全，而是要讲清楚“为什么用、怎么用、出问题怎么办”。
