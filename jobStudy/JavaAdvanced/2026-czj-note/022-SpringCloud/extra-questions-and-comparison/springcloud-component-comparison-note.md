# Spring Cloud 组件对比专题

## 1. 这份文档怎么用

这份文档专门准备横向对比题。

面试官问对比题时，不要只说 A 和 B 的定义。

建议按这个结构回答：

1. 两者都解决什么问题
2. 核心定位有什么不同
3. 项目里怎么选
4. 边界和取舍是什么

## 2. Spring Boot vs Spring Cloud

`Spring Boot` 主要解决单个应用的快速开发。

它关注：

- 自动配置
- Starter
- 内嵌容器
- 快速启动

`Spring Cloud` 主要解决微服务治理。

它关注：

- 注册发现
- 服务调用
- 网关
- 熔断限流降级
- 配置中心
- 分布式事务

面试说法：

> Spring Boot 是单个服务的开发基础，Spring Cloud 是多个服务之间的治理体系。

## 3. Spring Cloud vs Dubbo

`Spring Cloud` 更偏一整套微服务治理生态。

常见调用方式是 HTTP REST，也可以组合网关、注册中心、熔断限流等组件。

`Dubbo` 更偏 RPC 服务治理框架。

它关注高性能 RPC、服务治理、协议和序列化。

面试说法：

> Spring Cloud 更像微服务生态组合，Dubbo 更像 RPC 服务治理框架。两者都能做服务治理，但通信模型和技术体系不同。

## 4. Nacos vs Eureka

`Eureka` 是早期 Spring Cloud Netflix 体系里的注册中心。

`Nacos` 既能做注册中心，也常做配置中心。

Nacos 在国内 Spring Cloud Alibaba 项目里更常见。

面试说法：

> Eureka 更偏单一注册中心，Nacos 同时覆盖注册发现和配置管理，工程整合能力更强。

## 5. Ribbon vs LoadBalancer

`Ribbon` 是 Netflix 体系下的客户端负载均衡组件。

`Spring Cloud LoadBalancer` 是后续 Spring Cloud 官方推荐的客户端负载均衡方案。

面试说法：

> 两者都解决客户端负载均衡问题，但 Ribbon 属于早期 Netflix 体系，现在更多使用 Spring Cloud LoadBalancer。

## 6. OpenFeign vs RestTemplate

`RestTemplate` 更偏手动 HTTP 调用。

`OpenFeign` 更偏声明式接口调用。

面试说法：

> RestTemplate 要自己拼请求，Feign 用接口描述远程调用，更适合微服务内部服务调用。

## 7. OpenFeign vs Dubbo

`OpenFeign` 常见是 HTTP REST 调用。

`Dubbo` 更偏 RPC 框架。

面试说法：

> OpenFeign 更适合 Spring Cloud HTTP 体系，Dubbo 更偏高性能 RPC 和服务治理。两者不是简单优劣，而是调用模型不同。

## 8. Gateway vs Nginx

`Nginx` 更偏基础设施入口。

它适合：

- 反向代理
- 静态资源
- HTTPS
- 基础负载均衡

`Gateway` 更偏微服务网关。

它适合：

- 服务路由
- 鉴权
- 限流
- 灰度
- 链路治理

面试说法：

> Nginx 更靠近外部流量入口，Gateway 更靠近微服务治理，两者可以分层配合。

## 9. Gateway vs Zuul

`Zuul 1.x` 更早，基于 Servlet 阻塞模型。

`Gateway` 基于 WebFlux、Reactor、Netty。

面试说法：

> Gateway 是更现代的响应式网关方案，和当前 Spring Cloud 生态结合更自然。

## 10. Sentinel vs Hystrix

`Hystrix` 更偏熔断隔离。

`Sentinel` 更偏流量治理。

Sentinel 能力包括：

- 限流
- 熔断降级
- 热点参数
- 系统保护
- 控制台规则配置

面试说法：

> Hystrix 解决熔断降级，Sentinel 更强调完整流量治理和规则控制。

## 11. Seata vs MQ 最终一致

`Seata` 更偏同步事务协调。

`MQ 最终一致` 更偏异步补偿。

面试说法：

> 如果业务要求较强一致，可以考虑 Seata；如果允许短时间不一致，MQ 加重试补偿通常更轻量。

## 12. 一句话总结

组件对比题不要背定义，要围绕问题、定位、适用场景和取舍来答。
