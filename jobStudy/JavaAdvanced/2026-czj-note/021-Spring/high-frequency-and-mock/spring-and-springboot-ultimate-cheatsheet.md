# Spring / Spring Boot 终极速背版

## 1. Spring 一句话

Spring 是 Java 后端项目的基础设施框架，核心能力是对象管理、依赖注入、AOP 增强、事务管理和 Web 请求处理。

## 2. Spring 主线

- IOC：对象交给容器管理
- DI：容器把依赖自动注入进去
- AOP：把事务、日志、权限等横切逻辑统一织入
- Bean 生命周期：对象从实例化到销毁经历什么
- MVC：请求为什么能走到 Controller

## 3. Spring 最核心的 5 题

1. 什么是 IOC
2. 什么是 AOP
3. `@Transactional` 为什么能生效
4. `@Transactional` 为什么会失效
5. Spring MVC 流程怎么讲

## 4. `@Transactional` 速背

- 本质：AOP + 代理
- 生效关键：调用经过 Spring 代理
- 常见失效：
- 同类内部自调用
- 异常被吃掉
- 异常类型没触发默认回滚
- Bean 没交给 Spring 管
- 异步切线程

## 5. `@Async` + `@Transactional`

- 核心点：事务很多时候跟线程上下文绑定
- `@Async` 会切线程
- 切线程后原事务上下文通常不会自然过去
- 面试关键：代理 + 线程切换 + 事务边界

## 6. Spring MVC 速背

- 请求进 `DispatcherServlet`
- `HandlerMapping` 找处理器
- `HandlerAdapter` 调 Controller
- Controller 返回结果
- 视图解析或消息转换

## 7. 常见注解速背

- 组件：`@Component`、`@Service`、`@Repository`、`@RestController`
- 注入：`@Autowired`、`@Resource`
- 配置：`@Configuration`、`@Bean`
- Web：`@RequestBody`、`@RequestParam`
- 增强：`@Transactional`、`@Validated`、`@ControllerAdvice`

## 8. 循环依赖速背

- 定义：A 依赖 B，B 又依赖 A
- 不是所有循环依赖都能解决
- 更常见能处理：单例 Bean 的属性注入循环依赖
- 构造器循环依赖更难处理
- 三级缓存的本质：提前暴露早期引用

## 9. Spring Boot 一句话

Spring Boot 不是替代 Spring，而是 Spring 生态上的快速开发和工程化整合方案。

## 10. Spring / Spring MVC / Spring Boot 关系

- Spring：基础能力底座
- Spring MVC：Web 层方案
- Spring Boot：启动、配置和整合层

## 11. Spring Boot 最核心的 5 题

1. 什么是 Spring Boot
2. 为什么有了 Spring 还要 Spring Boot
3. 什么是自动装配
4. `@SpringBootApplication` 是什么
5. `starter` 和自动装配什么关系

## 12. 自动装配速背

- 定义：根据依赖、配置和运行条件自动决定加载哪些配置类和 Bean
- 核心：按条件装配，不是无脑全配
- `@EnableAutoConfiguration`：开启自动装配能力
- 常见条件：
- `@ConditionalOnClass`
- `@ConditionalOnMissingBean`
- `@ConditionalOnProperty`

## 13. `starter` 速背

- `starter`：场景化依赖集合
- 作用：把某类功能常用依赖先带进来
- 和自动装配关系：
- `starter` 带依赖
- 自动装配让配置按条件生效

## 14. Spring Boot 启动流程速背

- 入口：`SpringApplication.run(...)`
- 准备环境
- 创建容器
- refresh 容器
- 自动装配和 Bean 初始化生效
- Runner 执行
- 应用 ready

## 15. 启动事件速背

- `ApplicationStartingEvent`
- `ApplicationEnvironmentPreparedEvent`
- `ApplicationContextInitializedEvent`
- `ApplicationPreparedEvent`
- `ApplicationStartedEvent`
- `ApplicationReadyEvent`
- `ApplicationFailedEvent`

一句话记忆：

> Started 不等于 Ready。

## 16. Spring Boot 版本差异速背

- 面试主线：2.x -> 3.x
- Java 基线：17+
- 底层基线：Spring Framework 6
- Jakarta：`javax.*` -> `jakarta.*`
- Security：Spring Security 6
- 配置属性迁移要检查
- 自动配置口径更新：不要只会说 `spring.factories`

## 17. 项目表达一句话

如果结合项目讲：

> Spring 更像运行时底座，Spring Boot 更像工程化整合方案。

## 18. 面试前最后必过的 8 题

1. 什么是 Spring
2. 什么是 IOC
3. 什么是 AOP
4. `@Transactional` 为什么能生效
5. `@Transactional` 为什么会失效
6. 什么是 Spring Boot
7. 什么是自动装配
8. Spring / Spring MVC / Spring Boot 三者关系

## 19. 一句话收尾

> 终极速背版的目标不是替代全部文档，而是让你在最后一轮复习时，能把最核心的主线、陷阱和项目表达一次过完。
