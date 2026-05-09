# Spring 高频对比笔记

## 1. 这份文档怎么用

这一篇不是重新讲主线，而是把 Spring 里最常被放在一起比较的概念、注解和组件统一拉平。

适合两种场景：

1. 你知道每个点，但一对比就容易说混
2. 面试官直接用“有什么区别”来问你

## 2. Spring vs Spring MVC vs Spring Boot

### 最稳的回答

> Spring 是基础框架底座，主要解决 IOC、AOP、事务这些基础能力；Spring MVC 是 Spring 在 Web 层的解决方案；Spring Boot 则是站在 Spring 生态上的快速开发和工程化整合方案。

### 一句话记忆

> Spring 是底座，Spring MVC 是 Web 层，Spring Boot 是整合和启动层。

## 3. IOC vs DI

### 最稳的回答

> IOC 是一种思想，强调对象创建和依赖管理交给容器；DI 是 IOC 的实现方式，也就是容器在创建对象时把它依赖的其他对象注入进去。

### 一句话记忆

> IOC 是理念，DI 是落地方式。

## 4. AOP vs OOP

### 最稳的回答

> OOP 主要解决对象建模和职责封装问题，强调把业务逻辑放到对象和类里；AOP 则更适合处理事务、日志、权限这类横切逻辑，把这些通用能力从业务代码里抽离出来做统一增强。

### 一句话记忆

> OOP 管业务建模，AOP 管横切增强。

## 5. BeanFactory vs ApplicationContext

### 最稳的回答

> `BeanFactory` 可以理解成更基础的容器接口，核心是 Bean 获取和管理；`ApplicationContext` 是更常用、更完整的容器，除了 Bean 管理外，还整合了国际化、事件发布、资源访问等更多能力。平时项目里更常直接接触的是 `ApplicationContext`。

### 一句话记忆

> `BeanFactory` 更基础，`ApplicationContext` 更完整、更常用。

## 6. `@Autowired` vs `@Resource`

### 最稳的回答

> `@Autowired` 更偏 Spring 原生体系，默认更常被理解为按类型注入；`@Resource` 是标准注解，常被理解为按名称注入。两者都能做依赖注入，但 Spring 项目里更常见 `@Autowired`。

### 一句话记忆

> 一个更偏 Spring 原生，一个更偏标准注解。

## 7. `@Component` vs `@Bean`

### 最稳的回答

> `@Component` 更适合标在类上，通过组件扫描把对象注册进容器；`@Bean` 一般写在配置类的方法上，用来显式把方法返回对象注册成 Bean。前者更像“扫描发现”，后者更像“手动声明注册”。

### 一句话记忆

> `@Component` 靠扫描，`@Bean` 靠配置类方法。

## 8. `@Controller` vs `@RestController`

### 最稳的回答

> `@Controller` 更常用于传统 MVC 页面场景；`@RestController` 更适合前后端分离项目，它可以理解成 `@Controller + @ResponseBody`，通常直接返回 JSON。

### 一句话记忆

> 一个偏页面，一个偏 JSON。

## 9. `@RequestBody` vs `@RequestParam`

### 最稳的回答

> `@RequestBody` 用来接收请求体里的 JSON 数据；`@RequestParam` 一般用于接收 URL 查询参数或者表单参数。复杂对象更常见用 `@RequestBody`，简单条件查询更常见用 `@RequestParam`。

### 一句话记忆

> 一个接请求体，一个接查询参数。

## 10. `@ResponseBody` vs `@RestController`

### 最稳的回答

> `@ResponseBody` 一般标在方法上，表示把返回值直接写到响应体；`@RestController` 一般标在类上，相当于统一给这个类的方法加上了 `@ResponseBody`。

### 一句话记忆

> 一个常标方法，一个常标类。

## 11. `ApplicationRunner` vs `CommandLineRunner`

### 最稳的回答

> 两者都是 Spring Boot 应用启动后执行逻辑的入口，区别主要在参数封装方式。`CommandLineRunner` 接收原始字符串数组参数，`ApplicationRunner` 接收封装后的 `ApplicationArguments`。

### 一句话记忆

> 一个拿原始参数，一个拿封装参数。

## 12. Listener vs Runner

### 最稳的回答

> Listener 更偏事件监听，也就是在某个启动阶段收到通知；Runner 更偏启动末尾执行逻辑的入口。两者都和启动相关，但职责不一样。

### 一句话记忆

> Listener 负责“听阶段”，Runner 负责“跑逻辑”。

## 13. `ApplicationStartedEvent` vs `ApplicationReadyEvent`

### 最稳的回答

> `ApplicationStartedEvent` 表示容器 refresh 已经完成，但 `ApplicationRunner` / `CommandLineRunner` 还没执行完；`ApplicationReadyEvent` 更晚，表示应用已经真正 ready，更接近可以正式对外服务。

### 一句话记忆

> Started 不等于 Ready。

## 14. `starter` vs 自动装配

### 最稳的回答

> `starter` 更偏依赖整合，负责把某类场景常用依赖带进来；自动装配更偏配置生效，负责让这些依赖对应的配置按条件生效。

### 一句话记忆

> `starter` 带材料，自动装配拼材料。

## 15. Spring 事务 vs 数据库事务

### 最稳的回答

> Spring 事务更多是在应用层统一管理事务边界，核心是通过 AOP 和代理把事务控制织入业务方法；数据库事务则是数据库层面对提交、回滚、一致性和隔离性的底层支持。两者不是对立关系，而是应用层管理和数据库层能力的配合。

### 一句话记忆

> Spring 管事务边界，数据库提供事务能力。

## 16. 同步事务 vs `@Async` 场景下事务

### 最稳的回答

> 同步事务很多时候和当前线程上下文绑定，而 `@Async` 的核心是切线程，所以两者组合时更容易出现“原线程事务上下文没有传过去”的问题。

### 一句话记忆

> 事务跟线程走，异步会换线程。

## 17. Profile vs 配置覆盖

### 最稳的回答

> Profile 更偏“按环境分组切配置”，比如 dev、test、prod；配置覆盖则更偏“同一个配置项来自多个来源时，谁优先级更高”。一个是环境切换维度，一个是来源优先级维度。

### 一句话记忆

> Profile 管环境分组，覆盖规则管来源优先级。

## 18. Spring Boot 2.x vs 3.x

### 最稳的回答

> 面试里最值得讲的是 2.x 到 3.x 的主线变化：Java 基线提升到 17，底层切到 Spring Framework 6，Jakarta 命名空间从 `javax.*` 到 `jakarta.*`，再加上自动配置口径和部分依赖生态的变化。

### 一句话记忆

> Boot 3 的核心变化是 Java 17、Framework 6、Jakarta。

## 19. 怎么练这些对比最有效

建议练法：

1. 每次只抽一个对比项
2. 强迫自己先说一句话版
3. 再补 20 秒解释
4. 不要一上来讲太长

对比题最怕的不是不会，而是“知道很多，但说不清差别”。

## 20. 一句话收尾

> 对比题真正考的不是记忆量，而是你能不能把概念边界讲清，让面试官听出来你没混。
