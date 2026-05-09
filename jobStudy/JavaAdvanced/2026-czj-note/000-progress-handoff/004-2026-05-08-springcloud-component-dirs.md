# 2026-05-08 Spring Cloud 组件专题目录记录

## 1. 本次做了什么

本次在 `022-SpringCloud` 下拆出了组件专题子目录。

新增目录：

1. `nacos/`
2. `openfeign-loadbalancer/`
3. `gateway/`
4. `sentinel/`
5. `seata/`

每个目录先放了 `README.md`，用于说明后续整理方向。

## 2. 为什么这样拆

`Spring Cloud` 组件较多，如果全部放在顶层，后面高频题、回答包、对比题和项目追问会很快混在一起。

所以先按组件职责拆目录：

- `Nacos`：注册中心和配置中心
- `OpenFeign / LoadBalancer`：服务调用和负载均衡
- `Gateway`：统一入口
- `Sentinel`：熔断限流降级
- `Seata`：分布式事务

## 3. 后续建议

后续可以先从 `nacos/` 开始补，因为注册中心和配置中心是 `Spring Cloud` 面试里最容易先问到的基础能力。

## 4. 一句话总结

`Spring Cloud` 现在已经从顶层基础文档，进入到按组件拆专题的阶段。
