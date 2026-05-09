# Gateway 专题

## 1. 这个目录放什么

这个目录专门整理 `Spring Cloud Gateway` 相关内容。

主要围绕：

- 统一入口
- 路由转发
- 鉴权
- 限流
- 过滤器
- 网关和 `Nginx` 对比

## 2. 为什么要单独拆

网关在微服务里很容易被追问。

面试官常会从这些角度问：

- 为什么需要网关
- 网关放在什么位置
- 网关能做哪些统一能力
- 网关会不会成为瓶颈
- 网关和 `Nginx` 有什么区别

所以单独拆目录更清楚。

## 3. 后续准备补什么

当前已经按这个顺序整理：

1. `Gateway` 基础介绍
2. 路由、断言、过滤器
3. 鉴权、限流、灰度场景
4. `Gateway` 和 `Nginx` 对比
5. 网关项目场景回答

## 4. 当前已有文件

- [gateway-basic-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-basic-note.md)
- [gateway-route-filter-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-route-filter-note.md)
- [gateway-auth-limit-gray-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-auth-limit-gray-note.md)
- [gateway-advanced-questions-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-advanced-questions-note.md)
- [gateway-project-scenario-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-project-scenario-note.md)
- [gateway-vs-nginx-note.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-vs-nginx-note.md)
- [gateway-low-frequency-bonus-qa.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-low-frequency-bonus-qa.md)
- [gateway-mock-oral-script.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-mock-oral-script.md)
- [gateway-high-frequency-qa.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-high-frequency-qa.md)
- [gateway-answer-pack-0-1min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-answer-pack-0-1min.md)
- [gateway-answer-pack-0-3min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/022-SpringCloud/gateway/gateway-answer-pack-0-3min.md)

## 5. 面试主线怎么讲

建议按这个顺序讲：

1. 微服务拆分后，客户端不适合直接访问多个服务
2. Gateway 提供统一入口
3. 路由、断言、过滤器完成请求匹配、转发和前后处理
4. 网关层可以统一做鉴权、限流、日志、跨域和灰度
5. Gateway 和 Nginx 不是替代关系，而是职责分层
6. Gateway 本身也要多实例部署，避免入口单点

## 6. 当前先记住什么

先记住下面几句话：

1. Gateway 是微服务统一入口
2. 路由决定转发到哪里
3. 断言决定是否匹配路由
4. 过滤器决定请求前后做什么
5. 网关适合做通用入口治理，不适合堆复杂业务逻辑
6. Nginx 更偏基础入口，Gateway 更偏微服务治理

## 7. 一句话总结

`Gateway` 这条线的核心，是讲清楚“微服务为什么需要统一入口，以及入口层能承接哪些通用能力”。
