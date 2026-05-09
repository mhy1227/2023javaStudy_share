# Spring 一页速背版

## 1. Spring 核心一句话

Spring 是 Java 后端里非常核心的基础框架，核心价值是对象管理、依赖注入、AOP 增强、事务管理以及和各种基础能力的整合。

## 2. Spring 主线

- IOC：对象交给容器管理
- DI：容器把依赖自动注入进去
- AOP：把事务、日志、权限这类通用逻辑统一织入
- Bean 生命周期：对象从实例化到销毁经历什么
- MVC：请求为什么能走到 Controller
- Boot：项目为什么能更快整合和启动

## 3. IOC / DI

- IOC：控制反转，对象创建和依赖管理交给容器
- DI：IOC 的实现方式，容器在创建对象时把依赖一起注入
- 常见注入：构造器、Setter、字段
- 面试稳法：更推荐构造器注入，因为依赖明确、利于测试

## 4. AOP

- AOP：面向切面编程
- 核心：不改业务代码，统一织入横切逻辑
- 横切逻辑：事务、日志、权限、监控
- 一句话：业务方法管业务，通用逻辑交给切面增强

## 5. Bean / 生命周期

- Bean：交给 Spring 容器管理的对象
- 生命周期主干：实例化 -> 依赖注入 -> 初始化 -> 可用 -> 销毁
- 面试别一上来堆接口名，先把主干说顺

## 6. 事务

- Spring 事务本质：AOP + 代理
- `@Transactional` 生效关键：调用经过 Spring 代理
- 事务边界：一般放在 Service 层
- 传播行为：描述当前方法和已有事务怎么配合
- 最常见：`REQUIRED`、`REQUIRES_NEW`
- 默认认知：不是所有异常都会自动回滚

## 7. 事务失效

- 核心原因：没走代理、异常没正确传播、执行上下文变了
- 高频坑：
- 同类内部自调用
- 异常被吃掉
- 异常类型没触发默认回滚
- Bean 没交给 Spring 管
- 异步 / 多线程切线程

## 8. Spring MVC

- 主流程：
- 请求进 `DispatcherServlet`
- `HandlerMapping` 找处理器
- `HandlerAdapter` 调 Controller
- Controller 返回结果
- 视图解析或消息转换
- 关键词：
- `DispatcherServlet`：前端控制器 / 总入口
- `HandlerMapping`：找人
- `HandlerAdapter`：调方法

## 9. 常见注解

- 组件注册：`@Component`、`@Service`、`@Repository`、`@RestController`
- 依赖注入：`@Autowired`、`@Resource`
- 配置类：`@Configuration`、`@Bean`、`@Value`、`@ConfigurationProperties`
- Web 层：`@RequestMapping`、`@RequestBody`、`@RequestParam`、`@PathVariable`
- 增强类：`@Transactional`、`@Validated`、`@ControllerAdvice`、`@ExceptionHandler`

## 10. 高频注解对比

- `@Autowired` vs `@Resource`
- 前者更偏 Spring 原生、常按类型
- 后者是标准注解、常被理解为按名称

- `@Component` vs `@Bean`
- 前者更适合类扫描注册
- 后者更适合配置类里手动注册对象

- `@RequestBody` vs `@RequestParam`
- 前者接 JSON 请求体
- 后者接查询参数 / 表单参数

- `@ResponseBody` vs `@RestController`
- 前者常标方法
- 后者常标类，相当于统一加了前者

## 11. 循环依赖

- 定义：A 依赖 B，B 又依赖 A
- 不是所有循环依赖都能解决
- 更常见能处理：单例 Bean 的属性注入循环依赖
- 构造器循环依赖更难处理
- 面试说三级缓存时，别只背名字，要知道本质是提前暴露早期引用

## 12. Spring Boot

- 不是替代 Spring，而是快速开发和工程化整合方案
- Spring：基础能力
- Spring MVC：Web 层
- Spring Boot：快速整合和启动
- 约定优于配置：常见场景先给默认方案

## 13. 自动装配

- 定义：根据依赖、配置、运行条件自动决定加载哪些配置类和 Bean
- 核心：按条件装配，不是全都装
- 启动入口：`@SpringBootApplication`
- 核心能力：`@EnableAutoConfiguration`
- 常见条件注解：
- `@ConditionalOnClass`
- `@ConditionalOnMissingBean`
- `@ConditionalOnProperty`

## 14. starter

- `starter`：场景化依赖集合
- 作用：把某类功能常用依赖先准备好
- 和自动装配关系：
- `starter` 负责带依赖
- 自动装配负责让配置按条件生效

## 15. 最后必背 10 题

1. 什么是 Spring
2. 什么是 IOC
3. 什么是 AOP
4. `@Transactional` 为什么能生效
5. `@Transactional` 为什么会失效
6. Spring MVC 流程
7. 常见注解怎么分类讲
8. 循环依赖怎么理解
9. 什么是 Spring Boot
10. 什么是自动装配
