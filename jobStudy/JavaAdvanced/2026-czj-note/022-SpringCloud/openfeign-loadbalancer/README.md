# OpenFeign 与 LoadBalancer 专题

## 1. 这个目录放什么

这个目录专门整理服务调用和负载均衡相关内容。

主要围绕：

- `OpenFeign`
- `LoadBalancer`
- 服务间调用流程
- 客户端负载均衡
- 超时、重试、降级

## 2. 为什么放在一起

因为微服务调用时，通常不是只问“怎么发请求”，还会继续追：

- 调哪个服务
- 服务有多个实例时怎么选
- 调用失败怎么办
- 超时、重试怎么处理
- 下游异常时怎么保护上游

所以 `OpenFeign` 和负载均衡天然是一条线。

## 3. 当前已有文件

- [openfeign-loadbalancer-basic-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/openfeign-loadbalancer-basic-note.md)
- [openfeign-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/openfeign-note.md)
- [openfeign-advanced-notes.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/openfeign-advanced-notes.md)
- [loadbalancer-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/loadbalancer-note.md)
- [service-call-flow-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/service-call-flow-note.md)
- [timeout-retry-fallback-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/timeout-retry-fallback-note.md)
- [openfeign-loadbalancer-high-frequency-qa.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/openfeign-loadbalancer-high-frequency-qa.md)
- [openfeign-loadbalancer-answer-pack-0-1min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/openfeign-loadbalancer-answer-pack-0-1min.md)
- [openfeign-loadbalancer-answer-pack-0-3min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/openfeign-loadbalancer/openfeign-loadbalancer-answer-pack-0-3min.md)

## 4. 面试主线怎么讲

建议按这个顺序讲：

1. 微服务拆分后，服务之间从本地调用变成远程调用
2. `OpenFeign` 负责把远程 HTTP 调用封装成接口调用
3. 注册中心负责提供目标服务实例列表
4. `LoadBalancer` 负责从多个实例里选择一个
5. 远程调用还要考虑超时、重试、熔断和降级

## 5. 当前先记住什么

先记住下面几句话：

1. `OpenFeign` 解决的是服务之间怎么更方便地发起远程调用
2. `LoadBalancer` 解决的是多个实例时本次请求打到哪个实例
3. `Nacos` 提供实例列表，`LoadBalancer` 选择实例
4. `Feign` 写法像本地调用，但本质还是远程 HTTP 调用
5. 远程调用必须考虑失败、超时、重试和降级

## 6. 一句话总结

这一目录的核心，是讲清楚“服务之间怎么调用，以及多个服务实例时请求怎么分配”。
