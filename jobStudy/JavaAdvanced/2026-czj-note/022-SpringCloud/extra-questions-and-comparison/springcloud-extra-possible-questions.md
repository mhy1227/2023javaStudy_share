# Spring Cloud 额外可能问题清单

## 1. 这份文档补什么

核心组件已经覆盖：

- `Nacos`
- `OpenFeign`
- `LoadBalancer`
- `Gateway`
- `Sentinel`
- `Seata`

这份文档补一些牛客、LeetCode、实习僧等面经里可能出现的横向问题。

## 2. Spring Cloud 和 Spring Boot 有什么区别？

回答方向：

- Spring Boot 解决快速开发和自动配置
- Spring Cloud 解决微服务治理
- Spring Boot 是单个服务开发基础
- Spring Cloud 是多个服务之间的协作治理

一句话：

> Spring Boot 让单个应用更容易开发，Spring Cloud 让多个服务更容易协作。

## 3. Spring Cloud 和 Dubbo 有什么区别？

回答方向：

- Spring Cloud 更偏微服务治理全家桶
- Dubbo 更偏高性能 RPC 和服务治理
- Spring Cloud 常见 HTTP REST
- Dubbo 常见 RPC 协议

一句话：

> Spring Cloud 更像微服务生态组合，Dubbo 更像 RPC 服务治理框架。

## 4. Spring Cloud Netflix 和 Spring Cloud Alibaba 有什么区别？

回答方向：

- Netflix：Eureka、Ribbon、Hystrix、Zuul
- Alibaba：Nacos、Sentinel、Seata
- Netflix 很多组件逐渐停更或进入维护
- Alibaba 在国内项目里更常见

一句话：

> Netflix 体系是早期经典方案，Alibaba 体系更贴近国内常见实践。

## 5. 为什么 Ribbon 被 LoadBalancer 替代？

回答方向：

- Ribbon 属于 Netflix 体系
- Spring Cloud 后续推荐 Spring Cloud LoadBalancer
- LoadBalancer 更符合当前 Spring Cloud 生态演进

一句话：

> Ribbon 是早期客户端负载均衡方案，现在更多使用 Spring Cloud LoadBalancer。

## 6. 为什么 Hystrix 被 Sentinel 替代？

回答方向：

- Hystrix 更偏熔断隔离
- Sentinel 更强调流量治理
- Sentinel 支持流控、热点参数、系统保护、控制台等
- 国内 Spring Cloud Alibaba 项目更常用 Sentinel

一句话：

> Hystrix 偏熔断降级，Sentinel 更偏完整流量治理。

## 7. Gateway 和 Zuul 有什么区别？

回答方向：

- Zuul 1.x 基于 Servlet 阻塞模型
- Gateway 基于 WebFlux / Reactor / Netty
- Gateway 更适合当前 Spring Cloud 生态
- Gateway 的过滤器、路由能力更现代

一句话：

> Gateway 是 Spring Cloud 后续更推荐的响应式网关方案。

## 8. 微服务拆分原则是什么？

回答方向：

- 按业务边界拆分
- 单一职责
- 高内聚低耦合
- 数据尽量服务自治
- 不要一上来过度拆分

一句话：

> 微服务拆分不是越细越好，而是按业务边界和团队维护能力拆。

## 9. 微服务之间能不能直接查对方数据库？

回答方向：

- 不建议
- 会破坏服务边界
- 数据模型变化会影响其他服务
- 应该通过接口或事件交互

一句话：

> 服务可以调用服务接口，但不应该直接查对方库。

## 10. 微服务调用链怎么排查问题？

回答方向：

- 日志 traceId
- 网关日志
- Feign 调用日志
- Sentinel 监控
- 链路追踪工具
- 服务指标和告警

一句话：

> 排查微服务问题要沿请求链路看，而不是只看单个服务日志。

## 11. 微服务是不是一定比单体好？

回答方向：

- 不是
- 单体适合早期和小团队
- 微服务适合复杂业务和多团队协作
- 微服务会带来治理成本

一句话：

> 微服务不是银弹，是用复杂度换扩展性和协作效率。

## 12. Spring Cloud 项目里最容易出问题的地方？

回答方向：

- 服务调用超时
- 注册中心实例异常
- 配置不一致
- 网关路由错误
- 下游慢导致雪崩
- 跨服务事务不一致

一句话：

> 微服务的问题通常不在单个组件，而在服务之间的调用链和治理边界。

## 13. 一句话总结

额外问题主要围绕横向对比、服务拆分原则、版本演进和线上排查。
