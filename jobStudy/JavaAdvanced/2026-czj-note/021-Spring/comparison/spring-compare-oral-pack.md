# Spring 高频对比口语包

## 1. 这份文档怎么用

这一篇不是速记版，也不是详细展开版，而是更接近真实一面口语表达的版本。

你可以这样理解三篇文档的分工：

- `spring-compare-note.md`：速记版
- `spring-compare-long-answer-note.md`：详细展开版
- `spring-compare-oral-pack.md`：口语版

如果你现在的问题是：

> 我知道区别，但说出来还是有点像背书。

那这一篇最适合你。

## 2. Spring vs Spring MVC vs Spring Boot

### 口语版

> 这三个我一般会理解成三层。Spring 是底座，解决 IOC、AOP、事务这些基础能力；Spring MVC 是 Spring 在 Web 层的方案，主要负责请求处理；Spring Boot 则是在 Spring 生态上继续做工程化整合，让项目更快启动、更方便配置。所以它们不是互相替代，而是底座、Web 层和整合层的关系。

## 3. IOC vs DI

### 口语版

> 这两个我一般不会混着讲。IOC 更像一种思想，就是对象创建和依赖管理交给容器；DI 是它的落地方式，也就是容器在创建对象时把依赖一起注入进去。所以一个偏理念，一个偏实现。

## 4. AOP vs OOP

### 口语版

> OOP 更像是在做业务建模，把职责放到类和对象里；AOP 则更适合处理事务、日志、权限这种横切逻辑。也就是说，OOP 主要管业务结构，AOP 主要管通用增强。

## 5. BeanFactory vs ApplicationContext

### 口语版

> 我一般会把 `BeanFactory` 理解成更基础的容器接口，`ApplicationContext` 理解成更完整、项目里更常用的容器。后者除了 Bean 管理，还把事件、资源访问这些能力也整合进来了。

## 6. `@Autowired` vs `@Resource`

### 口语版

> 这两个都能做依赖注入，但 `@Autowired` 更偏 Spring 原生体系，平时更常见；`@Resource` 是标准注解，大家一般会把它理解成更偏按名称注入。所以如果面试官问区别，我会先从来源和默认匹配思路去讲。

## 7. `@Component` vs `@Bean`

### 口语版

> `@Component` 更像通过扫描自动发现并注册对象，适合标在类上；`@Bean` 更像在配置类里手动声明注册一个对象，特别适合第三方组件或者需要自定义初始化逻辑的对象。

## 8. `@Controller` vs `@RestController`

### 口语版

> `@Controller` 更偏传统页面场景，`@RestController` 更偏前后端分离接口场景。后者本质上可以理解成 `@Controller + @ResponseBody`，所以通常直接返回 JSON。

## 9. `@RequestBody` vs `@RequestParam`

### 口语版

> `@RequestBody` 主要是接请求体里的 JSON，对应复杂对象提交；`@RequestParam` 更常见接 URL 参数或者表单参数，对应简单条件查询。所以一个更偏请求体反序列化，一个更偏普通参数提取。

## 10. `@ResponseBody` vs `@RestController`

### 口语版

> `@ResponseBody` 一般是方法级别，表示直接把返回值写到响应体里；`@RestController` 一般是类级别，相当于统一给这个类的方法加上了 `@ResponseBody`。所以前后端分离项目里，我一般更常用 `@RestController`。

## 11. `ApplicationRunner` vs `CommandLineRunner`

### 口语版

> 这两个我会先说结论：作用很像，都是启动后执行逻辑的钩子，区别主要在参数。`CommandLineRunner` 拿原始参数，`ApplicationRunner` 拿封装后的参数对象。

## 12. Listener vs Runner

### 口语版

> 这两个都跟启动有关，但不是一回事。Listener 更偏监听启动过程中的某个阶段事件，Runner 更偏应用启动到最后阶段时执行一段逻辑。一个是“听事件”，一个是“跑逻辑”。

## 13. `ApplicationStartedEvent` vs `ApplicationReadyEvent`

### 口语版

> 这两个最容易混。`ApplicationStartedEvent` 更早，说明容器 refresh 完了，但 Runner 还没跑完；`ApplicationReadyEvent` 更晚，表示应用真正 ready，更接近可以开始对外服务。所以我一般会强调一句：Started 不等于 Ready。

## 14. `starter` vs 自动装配

### 口语版

> `starter` 更偏依赖整合，负责把某类场景常用依赖先带进来；自动装配更偏配置生效，负责让这些依赖对应的配置按条件真正接起来。所以一句话说就是：`starter` 带材料，自动装配拼材料。

## 15. Spring 事务 vs 数据库事务

### 口语版

> Spring 事务更像应用层统一管理事务边界，通过 AOP 和代理把事务控制织入业务方法；数据库事务则是数据库本身提供的提交、回滚和隔离能力。两者不是冲突，而是应用层控制和底层能力的配合。

## 16. 同步事务 vs `@Async` 场景下事务

### 口语版

> 这题我一般先想到线程。同步事务很多时候和当前线程上下文绑定，而 `@Async` 会切线程，所以组合起来时容易出现原来的事务上下文没有过去的问题。本质上考的是线程切换和事务边界。

## 17. Profile vs 配置覆盖

### 口语版

> Profile 更偏按环境切换配置，比如 dev、test、prod；配置覆盖更偏同一个配置项来自多个来源时，最终谁优先级更高。所以一个是环境分组问题，一个是来源优先级问题。

## 18. Spring Boot 2.x vs 3.x

### 口语版

> 如果按面试里最常讲的主线，我一般会抓几件事：Java 基线提升到 17、底层切到 Spring Framework 6、Jakarta 从 `javax.*` 切到 `jakarta.*`，再加上一些自动配置和依赖生态的变化。也就是说，Boot 3 不只是版本号变了，技术基线也一起抬了。

## 19. 这篇怎么练

建议练法：

1. 每次只抽一个对比项
2. 强迫自己先不看文档口述
3. 说卡了再回来对照这一篇
4. 控制在 20 秒到 40 秒一题

这样更接近真实一面。

## 20. 一句话收尾

> 对比题口语版的核心，不是把定义背得多准，而是让面试官听出来你确实知道边界在哪里。
