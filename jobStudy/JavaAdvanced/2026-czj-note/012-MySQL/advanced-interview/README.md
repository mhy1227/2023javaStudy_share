# MySQL 进阶面试

## 1. 为什么要单独开这一组文档

基础 MySQL 面试通常会问：

- 索引
- 事务
- MVCC
- 锁
- redo log / undo log / binlog
- SQL 执行流程
- 慢 SQL 排查

但真实面试里经常不会停在这里。

很多时候面试官会继续往下追：

- 主从复制
- 读写分离
- 分库分表
- 深分页
- 大表优化
- `count(*)` 问题
- Buffer Pool
- 热点更新
- 一致性和高可用

所以这一组文档专门承接“基础问完之后的进阶追问”。

## 2. 这一组文档和顶层 MySQL 文档的关系

- 顶层文档：更偏基础主线和常规面试。
- 这里的文档：更偏中高级面试追问、场景题和架构题。

## 3. 当前文件

- `mysql-advanced-high-frequency.md`
- `mysql-advanced-answers.md`
- `mysql-advanced-review-checklist.md`
- `mysql-final-review.md`
- `mysql-replication-readwrite-note.md`
- `mysql-sharding-bigtable-note.md`
- `mysql-buffer-pool-note.md`
- `mysql-performance-scenarios-note.md`
- `mysql-lock-traps-note.md`
- `mysql-lock-oral-answers.md`
- `mysql-mock-chain-questions.md`
- `high-frequency-supplement/README.md`

## 4. 这一层新增的三篇文档怎么理解

这次新补进来的三篇，更偏“基础锁问完之后，面试官继续往下追”的部分：

- `mysql-lock-traps-note.md`
  主要整理锁相关的易错追问、陷阱题和变体题
- `mysql-lock-oral-answers.md`
  主要整理锁专题的口语化回答
- `mysql-mock-chain-questions.md`
  主要把索引、事务、MVCC、锁、日志、主从复制这些点串成连环追问链

可以把它们理解成：

- 不是基础定义文档
- 而是面向中高级面试表现力的补充材料

## 5. 建议怎么阅读这一层

建议顺序：

1. 先看 `mysql-advanced-high-frequency.md`
2. 再看 `mysql-advanced-answers.md`
3. 再看 `mysql-final-review.md`，建立一条总主线
4. 然后按专题看复制、分库分表、Buffer Pool、性能场景
5. 最后看锁追问、锁口语版、模拟连环追问
6. 如果还想补高频变体题，再看 `high-frequency-supplement/README.md`

## 6. 后续建议可继续拆的专题

如果后面继续补，可以继续拆成：

- 主从复制与读写分离
- 分库分表
- Buffer Pool 与内存命中
- 大表与深分页优化
- 高并发更新与热点行问题
