# Seata 专题

## 1. 这个目录放什么

这个目录专门整理 `Seata` 和分布式事务相关内容。

主要围绕：

- 本地事务和分布式事务
- 跨服务数据一致性
- `Seata` 基础定位
- `AT` 模式粗理解
- 分布式事务的取舍

## 2. 为什么要单独拆

分布式事务本身就是微服务面试里的重点。

面试官一般不会只问“`Seata` 是什么”，更容易问：

- 为什么微服务事务会变难
- 本地事务为什么不够用
- 分布式事务有哪些方案
- `Seata` 解决了什么问题
- 为什么有些场景不建议硬上分布式事务

所以它适合单独拆成一条线。

## 3. 后续准备补什么

当前已经按这个顺序整理：

1. 分布式事务基础
2. `Seata` 基础介绍
3. `AT` 模式粗理解
4. 强一致和最终一致取舍
5. 项目场景回答

## 4. 当前已有文件

- [distributed-transaction-basic-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/distributed-transaction-basic-note.md)
- [seata-basic-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-basic-note.md)
- [seata-mode-comparison-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-mode-comparison-note.md)
- [seata-scenarios-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-scenarios-note.md)
- [seata-advanced-questions-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-advanced-questions-note.md)
- [seata-project-scenario-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-project-scenario-note.md)
- [seata-mock-oral-script.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-mock-oral-script.md)
- [seata-high-frequency-qa.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-high-frequency-qa.md)
- [seata-answer-pack-0-1min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-answer-pack-0-1min.md)
- [seata-answer-pack-0-3min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/seata/seata-answer-pack-0-3min.md)

## 5. 面试主线怎么讲

建议按这个顺序讲：

1. 微服务拆分后，订单、库存、账户会分散到不同服务
2. 本地事务已经管不了跨服务写数据
3. 分布式事务要协调多个参与者的提交和回滚
4. `Seata` 提供了常见的分布式事务协调方案
5. `AT`、`TCC`、`SAGA` 分别对应不同一致性和侵入程度
6. 不是所有场景都适合强一致，很多业务更适合最终一致
7. 项目里要讲清楚为什么用 Seata，以及为什么有些场景不用

## 6. 当前先记住什么

先记住下面几句话：

1. `Seata` 不是替代本地事务，而是协调多个本地事务
2. 分布式事务的核心问题是跨服务一致性
3. `AT` 偏自动协调，`TCC` 偏三段式控制，`SAGA` 偏补偿和最终一致
4. 不是所有业务都值得上分布式事务
5. 选型要先看业务一致性要求，再看成本
6. MQ 最终一致和 Seata 不是谁替代谁，而是适合不同一致性要求
7. TCC 的难点是幂等、空回滚和悬挂

## 7. 一句话总结

`Seata` 这条线的核心，是讲清楚“多服务一起改数据时，一致性为什么变难，以及可以怎么协调”。
