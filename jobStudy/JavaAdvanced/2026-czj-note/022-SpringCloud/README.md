# 022-SpringCloud

## 1. 这一章准备怎么补

`Spring Cloud` 这一章和前面的 `Spring`、`MySQL`、`Redis` 不太一样。

它不是单点知识，而更像一组“分布式系统常见问题”的工程化组合：

- 服务注册与发现
- 服务调用
- 负载均衡
- 配置中心
- 网关
- 熔断限流降级
- 链路追踪
- 分布式事务

所以这一章不适合一上来就按组件名单硬背，更适合围绕下面几条主线去整理：

1. 为什么单体项目会往微服务演进
2. 微服务拆开以后会多出哪些基础设施问题
3. `Spring Cloud` 常见组件分别在解决什么问题
4. 面试里怎么把“组件功能”讲成“系统问题 -> 解决方案 -> 代价与边界”

## 2. 当前目录说明

这一章先不追求一下子铺满，而是先把题库入口搭起来。

当前先放：

1. `README.md`
2. `springcloud-basic-note.md`
3. `springcloud-microservice-introduction-note.md`
4. `springcloud-core-components-note.md`
5. `springcloud-possible-questions.md`
6. `nacos/`
7. `openfeign-loadbalancer/`
8. `gateway/`
9. `sentinel/`
10. `seata/`
11. `high-frequency-and-mock/`

后面更自然的扩展顺序是：

1. Spring Cloud 高频问题
2. `0-1` 分钟回答包
3. `0-3` 分钟回答包
4. mock 追问脚本
5. 组件对比专题

## 3. 这一章最可能会覆盖什么

从面试角度，`Spring Cloud` 这章后续大概率会重点覆盖：

- `Nacos`
- `OpenFeign`
- `Gateway`
- `Ribbon` / `LoadBalancer`
- `Sentinel`
- `Seata`
- 配置中心
- 注册中心
- 微服务调用链
- 服务雪崩、熔断、限流、降级

如果后面要继续扩，也可以补：

- `Eureka` / `Zookeeper` / `Consul` 对比
- `Dubbo` 和 `Spring Cloud` 对比
- `Spring Boot` 和 `Spring Cloud` 的关系

## 4. 当前建议怎么开始

当前最适合的起点不是直接背组件 API，而是先把：

1. 什么是微服务
2. 为什么需要注册中心
3. 为什么需要配置中心
4. 为什么需要网关
5. 为什么会有熔断、限流、降级
6. 为什么分布式事务更难

这几类问题先讲顺。

## 5. 一句话总结

`Spring Cloud` 面试的关键，不是堆组件名，而是能不能把“微服务拆分后新增了哪些问题，以及这些组件分别在解决什么问题”讲清楚。
