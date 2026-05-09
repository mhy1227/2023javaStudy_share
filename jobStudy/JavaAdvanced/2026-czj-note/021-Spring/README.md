# 021-Spring

## 1. 这一章怎么学

Spring 这一章不适合一上来就扎进非常碎的源码细节。

更合适的顺序是：

1. 先知道 Spring 是什么，为什么 Java 后端离不开它。
2. 再理解 `IOC`、依赖注入、Bean 管理。
3. 再进入 `AOP`、代理、事务这条线。
4. 然后补 Bean 生命周期、循环依赖、常见注解。
5. 再补 Spring MVC 执行流程。
6. 最后再看 Spring Boot 自动装配、项目整合和高频追问。

这一章复习时，建议始终围绕下面这几条主线：

- 管理：Spring 为什么能帮你管理对象。
- 注入：对象之间的依赖为什么能自动串起来。
- 增强：为什么事务、日志、权限这类能力能统一织进去。
- 生命周期：Bean 从创建到销毁到底经历了什么。
- Web：一次请求为什么能走到 Controller。
- 启动：Spring Boot 为什么能把项目更快跑起来。

## 2. 当前目录说明

当前 `021-Spring` 下面已经放了一套从别处 copy 过来的 Spring 资料，放在：

- `005-Spring`

这套资料可以作为现成内容库继续复用。

但当前这套笔记的目标不是简单搬运，而是继续整理成统一版复习结构。所以顶层会逐步补齐：

- 入口文档
- 主线专题
- 高频问题
- 回答版
- checklist
- 模拟追问

## 3. 当前建议先看什么

当前阶段最适合按这条顺序看：

1. `spring-basic-overview.md`
2. `spring-ioc-di-note.md`
3. `spring-aop-note.md`
4. `spring-bean-lifecycle-note.md`
5. `spring-transaction-note.md`
6. `spring-transaction-invalid-note.md`
7. `spring-mvc-note.md`
8. `spring-common-annotations-note.md`
9. `spring-circular-dependency-note.md`
10. `springboot-basic-note.md`
11. `springboot-autoconfiguration-note.md`

如果你想对照现成素材一起看，再回头配合：

1. `005-Spring/01-Spring核心-IOC-AOP-Bean生命周期.md`
2. `005-Spring/02-Spring事务与@Transactional失效场景.md`
3. `005-Spring/03-SpringMVC执行流程.md`
4. `005-Spring/06-Spring高频追问-常见注解与面试回答.md`
5. `005-Spring/05-SpringBoot基础与自动装配.md`

## 4. 后续会逐步补哪些正式文档

当前 Spring 顶层主线已经补到了：

- `spring-basic-overview.md`
- `spring-ioc-di-note.md`
- `spring-aop-note.md`
- `spring-bean-lifecycle-note.md`
- `spring-transaction-note.md`
- `spring-transaction-invalid-note.md`
- `spring-mvc-note.md`
- `spring-common-annotations-note.md`
- `spring-circular-dependency-note.md`
- `springboot-basic-note.md`
- `springboot-autoconfiguration-note.md`

另外已经单独拆出一个子目录：

- `high-frequency-and-mock`

用于承接高频问答、口语化回答和后续 mock。

现在另外也补了一个对比专题子目录：

- `comparison`

用于统一整理高频“有什么区别”类问题。

后续更自然继续补的是：

- Spring 高频问答
- Spring Boot 高频追问
- Spring / Spring Boot mock

## 5. 先记住的一句话

> Spring 面试的核心不是死背注解，而是围绕 IOC、AOP、事务、Bean 生命周期、MVC 和自动装配这几条主线，解释清楚“对象为什么能被管理、依赖为什么能自动注入、通用能力为什么能统一增强”。 
