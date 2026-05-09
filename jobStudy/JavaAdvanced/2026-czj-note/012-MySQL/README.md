# 012-MySQL

## 1. 这一章怎么学

MySQL 这一章建议从基础主线开始，不要一上来就扎进特别碎的索引细节或者日志细节。

更合适的顺序是：

1. 先知道 MySQL 是干什么的。
2. 再理解为什么面试总爱问索引。
3. 再进入事务、隔离级别、MVCC。
4. 然后补锁、日志、执行流程、慢 SQL 排查。
5. 最后再做场景题、面试题、口语回答版。

这一章后续建议围绕下面这几条主线反复复习：

- 存储：MySQL 到底存了什么，为什么适合做业务数据持久化。
- 查询：一条 SQL 为什么快，为什么慢。
- 一致性：事务、隔离级别、锁、MVCC 怎么配合。
- 恢复与复制：redo log、undo log、binlog 分别做什么。
- 调优：索引优化、执行计划、慢 SQL 排查。

## 2. 当前目录说明

当前 `012-MySQL` 下已经有一批从旧资料中 copy 过来的素材，放在：

- `003-Mysql`
- `advanced-interview`

这批素材可以作为“现成内容库”继续复用。

但当前这套笔记的目标不是简单搬运，而是整理成统一版复习结构。所以顶层会逐步补齐更规范的入口文档、专题文档、面试回答文档和 checklist。

其中：

- `003-Mysql` 更偏旧资料和基础素材库
- `advanced-interview` 更偏中高级面试追问、场景题、口语回答和连环追问链

## 3. 当前建议先看什么

当前阶段最适合先看：

1. `mysql-basic-overview.md`
2. `003-Mysql/01-MySQL基础总览.md`
3. `003-Mysql/06-MySQL事务-ACID-隔离级别-MVCC.md`
4. `003-Mysql/05-MySQL执行流程与慢SQL排查.md`
5. `advanced-interview/README.md`

## 4. 后续会逐步补哪些文件

后续建议逐步整理出这些正式文档：

- `mysql-basic-overview.md`
- `mysql-index-note.md`
- `mysql-transaction-mvcc-note.md`
- `mysql-lock-note.md`
- `mysql-log-note.md`
- `mysql-explain-slow-sql-note.md`
- `mysql-interview-high-frequency.md`
- `mysql-interview-answers.md`
- `mysql-review-checklist.md`

## 5. 先记住的一句话

> MySQL 面试的核心不是死背命令，而是围绕索引、事务、锁、日志、执行流程这几条主线，解释清楚“为什么这样设计、为什么这样快、为什么会出问题、出了问题怎么排查”。
