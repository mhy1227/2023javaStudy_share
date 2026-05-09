# Sentinel 专题

## 1. 这个目录放什么

这个目录专门整理 `Sentinel` 相关内容。

主要围绕：

- 服务雪崩
- 熔断
- 限流
- 降级
- 系统保护

## 2. 为什么要单独拆

`Sentinel` 面试里通常不是只问“它是什么”，更容易追问：

- 为什么会有服务雪崩
- 熔断、限流、降级有什么区别
- 下游服务慢了怎么办
- 限流一般按什么维度做
- 熔断后怎么恢复

这些都属于稳定性治理，所以单独拆目录更合适。

## 3. 后续准备补什么

当前已经按这个顺序整理：

1. `Sentinel` 基础介绍
2. 服务雪崩
3. 熔断、限流、降级对比
4. 常见规则和场景
5. 项目场景回答

## 4. 当前已有文件

- [sentinel-basic-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/sentinel/sentinel-basic-note.md)
- [service-avalanche-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/sentinel/service-avalanche-note.md)
- [flow-control-circuit-breaker-degrade-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/sentinel/flow-control-circuit-breaker-degrade-note.md)
- [sentinel-rules-and-scenarios-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/sentinel/sentinel-rules-and-scenarios-note.md)
- [sentinel-high-frequency-qa.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/sentinel/sentinel-high-frequency-qa.md)
- [sentinel-answer-pack-0-1min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/sentinel/sentinel-answer-pack-0-1min.md)
- [sentinel-answer-pack-0-3min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/sentinel/sentinel-answer-pack-0-3min.md)

## 5. 面试主线怎么讲

建议按这个顺序讲：

1. 微服务调用链变长，局部故障容易扩散
2. 下游慢调用和异常可能引发服务雪崩
3. Sentinel 通过限流、熔断、降级保护系统
4. 限流解决流量过高，熔断解决依赖不稳定，降级解决失败兜底
5. 规则配置要结合压测、历史流量和业务优先级

## 6. 当前先记住什么

先记住下面几句话：

1. Sentinel 不是单纯限流工具，而是流量治理和服务保护组件
2. 服务雪崩的本质是局部故障没有及时止损
3. 限流挡流量，熔断断依赖，降级给兜底
4. Gateway 管入口，Feign 管调用，Sentinel 管保护
5. 降级结果必须业务可接受，核心写操作不能随便降级成成功

## 7. 一句话总结

`Sentinel` 这条线的核心，是讲清楚“微服务调用链不稳定时，系统怎么保护自己”。
