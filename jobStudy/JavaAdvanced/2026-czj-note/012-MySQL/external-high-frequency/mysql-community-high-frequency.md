# MySQL 社区高频题整理

## 1. 这份文档怎么来的

这一份不是凭空列题，而是结合公开面经里反复出现的题型整理出来的。

本次参考来源主要包括：

- 牛客讨论区
- LeetCode 中文站讨论区
- JavaGuide
- SegmentFault

## 2. 外部面经里反复出现的 MySQL 高频题

### 2.1 索引方向

外部面经里重复率最高的一组：

- 什么是索引？
- 为什么 MySQL 索引底层常说 B+ 树？
- 聚簇索引和二级索引有什么区别？
- 什么是回表？
- 什么是覆盖索引？
- 联合索引最左前缀原则是什么？
- 索引为什么会失效？
- 为什么有索引 SQL 还是慢？
- 为什么索引不是越多越好？

### 2.2 事务与 MVCC 方向

第二组高频：

- 什么是事务？
- ACID 是什么？
- 四种隔离级别是什么？
- MySQL 默认隔离级别是什么？
- 什么是脏读、不可重复读、幻读？
- MVCC 是什么？
- MVCC 想解决什么问题？
- 快照读和当前读是什么？
- MVCC 和锁是什么关系？

### 2.3 锁方向

第三组高频：

- 行锁和表锁有什么区别？
- InnoDB 行锁为什么和索引有关？
- 什么是共享锁和排他锁？
- 什么是记录锁、间隙锁、临键锁？
- 间隙锁和临键锁解决什么问题？
- 什么是死锁？怎么避免？

### 2.4 日志方向

第四组高频：

- redo log、undo log、binlog 分别是什么？
- redo log 和 binlog 有什么区别？
- 为什么既有 redo log，又有 binlog？
- 为什么 undo log 和 MVCC 有关系？
- 什么是两阶段提交？
- 为什么两阶段提交重要？

### 2.5 执行流程与排查方向

第五组高频：

- 一条 SQL 到 MySQL 后怎么执行？
- 连接器、解析器、优化器、执行器分别做什么？
- EXPLAIN 是干什么的？
- EXPLAIN 重点看哪些字段？
- 为什么不能只看有没有索引？
- 慢 SQL 一般怎么排查？

## 3. 外部面经里最常被串着问的链路

### 链路一：索引链路

- 什么是索引
- 为什么是 B+ 树
- 聚簇索引和二级索引
- 回表和覆盖索引
- 联合索引和最左前缀
- 索引失效

### 链路二：事务链路

- 什么是事务
- ACID
- 隔离级别
- 脏读/不可重复读/幻读
- MVCC
- 快照读/当前读
- 锁和 MVCC 的关系

### 链路三：日志链路

- redo log / undo log / binlog
- redo log 和 binlog 的区别
- 为什么要两阶段提交
- 两阶段提交解决什么问题

### 链路四：排查链路

- 一条 SQL 怎么执行
- EXPLAIN 看什么
- 慢 SQL 怎么排查
- 有索引为什么还是慢

## 4. 社区里最值得优先背的题

如果你只选最核心的一批，可以优先背：

1. 为什么 MySQL 索引底层常说 B+ 树。
2. 聚簇索引、二级索引、回表、覆盖索引。
3. 事务、ACID、默认隔离级别、MVCC。
4. 行锁、间隙锁、临键锁。
5. redo log、undo log、binlog、两阶段提交。
6. 一条 SQL 怎么执行。
7. EXPLAIN 看什么，慢 SQL 怎么排查。

## 5. 参考来源

- 牛客讨论区：`https://www.nowcoder.com/discuss/846045342515621888`
- 牛客讨论区：`https://www.nowcoder.com/discuss/353157820960940032`
- 牛客讨论区：`https://www.nowcoder.com/discuss/832569782716100608`
- LeetCode 中文站：`https://leetcode.cn/discuss/post/3448720/java-mysql-ji-wang-hou-duan-mian-shi-ba-bj8hd`
- LeetCode 中文站：`https://leetcode.cn/discuss/post/3158900/mian-jing-gun-bai-du-gun-javagun-hou-dua-7340`
- JavaGuide：`https://javaguide.cn/interview-preparation/backend-interview-plan.html`
- SegmentFault：`https://segmentfault.com/a/1190000045231138`