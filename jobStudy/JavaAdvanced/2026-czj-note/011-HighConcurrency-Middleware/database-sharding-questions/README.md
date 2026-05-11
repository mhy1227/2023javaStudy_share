# 数据库架构与分片追问

## 1. 这个子目录放什么

这一组文档专门放：

- 分库分表
- 横向拆分 / 纵向拆分
- 分片键
- 跨库查询
- 热点分片
- 扩容迁移

这类更偏数据库架构和数据分片的问题。

也就是说，它不是纯 SQL 题，也不是纯一致性题，而是：

- 数据库架构
- 分布式分片
- 高并发场景下的数据层扩展

## 2. 为什么单独拆子目录

因为 `011-HighConcurrency-Middleware` 顶层已经有：

- 主线文档
- 场景题
- mock
- checklist
- last-minutes

如果后面继续把“跨库 join 怎么答”“非分片键查询怎么答”“扩容迁移怎么答”这类单题继续平铺在顶层，会越来越乱。

所以更合理的方式是：

- 顶层保留总览和主线
- 子目录承接更细的专题追问

## 3. 当前适合继续补的方向

优先级最高的几类题通常是：

- 跨库 `join` 怎么答
- 非分片键查询怎么答
- 热点分片怎么答
- 扩容迁移怎么答
- 横向拆分 / 纵向拆分怎么答

当前已补：

- `cross-shard-join-and-non-sharding-key-query-note.md`
- `hot-shard-and-hotspot-note.md`
- `rebalance-and-migration-note.md`
- `sharding-key-selection-note.md`
- `horizontal-vs-vertical-sharding-answer-pack.md`

## 4. 一句话总结

这个子目录不是再讲“分库分表是什么”，而是专门收口“分库分表之后面试官最爱怎么追”。
