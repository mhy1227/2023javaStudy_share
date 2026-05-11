# Spring 常见注解笔记

## 1. 这份文档怎么用

这一篇不是单纯罗列注解名字，而是把面试里最常追问的注解按类别串起来：

- 组件注册类
- 依赖注入类
- 配置类
- Web 层类
- 事务与校验增强类
- 启动与扫描类

复习这篇时，重点不是背得越多越好，而是知道它们各自解决什么问题、项目里一般怎么用、面试官会往哪追。

## 2. 先记住最核心的 6 句

1. 面试里讲 Spring 注解，最好先分类，再结合项目举例。
2. `@Component` 是通用组件，`@Service`、`@Repository`、`@Controller`、`@RestController` 是更语义化的派生。
3. `@Autowired` 更偏 Spring 原生体系，默认按类型注入；`@Resource` 常被理解为按名称注入。
4. `@Configuration` + `@Bean` 更适合配置类和第三方组件注册。
5. `@RequestBody` 接 JSON 请求体，`@RequestParam` 接查询参数或表单参数。
6. `@RestController` 本质上可以理解成 `@Controller + @ResponseBody`。

## 3. 面试里先怎么总答

如果面试官问：

> 你项目里 Spring 常用哪些注解？

比较稳的一版是：

> 我一般会把 Spring 常用注解分成几类来看。第一类是组件注册类，比如 `@Component`、`@Service`、`@Repository`、`@Controller`、`@RestController`；第二类是依赖注入类，比如 `@Autowired`、`@Resource`；第三类是配置相关，比如 `@Configuration`、`@Bean`、`@Value`、`@ConfigurationProperties`；第四类是 Web 层接口相关，比如 `@RequestMapping`、`@GetMapping`、`@PostMapping`、`@RequestBody`、`@RequestParam`、`@PathVariable`；第五类是事务和增强相关，比如 `@Transactional`、`@Validated`、`@ControllerAdvice`、`@ExceptionHandler`；第六类是启动和扫描相关，比如 `@SpringBootApplication`、`@ComponentScan`、`@MapperScan`。如果结合我的项目，最常用的还是 `@Service`、`@RestController`、`@Autowired`、`@RequestBody`、`@Transactional` 这些。 

这段话的价值在于先把节奏控住。

## 4. 组件注册类注解怎么讲

### `@Component`

> `@Component` 是通用组件注解，表示把当前类交给 Spring 容器管理。

### `@Service`

> `@Service` 一般标在业务层，本质上和 `@Component` 类似，但语义更清晰，便于分层管理。

### `@Repository`

> `@Repository` 一般用于持久层或数据访问层，语义上表示这是数据访问组件。

### `@Controller`

> `@Controller` 更常用于传统 MVC 场景，通常返回页面视图。

### `@RestController`

> `@RestController` 更适合前后端分离项目，它可以理解成 `@Controller + @ResponseBody`，返回的通常是 JSON。

## 5. 依赖注入类注解怎么讲

### `@Autowired`

> `@Autowired` 是 Spring 常用的自动注入注解，默认按类型注入。

面试里可以顺手补一句：

> 它可以标在字段、构造器、Setter 上，不过现在更推荐构造器注入，因为依赖关系更明确，也更利于测试。

### `@Resource`

> `@Resource` 是标准注解，常被理解为默认更偏向按名称注入。

### `@Autowired` 和 `@Resource` 区别怎么答

可以直接背：

> `@Autowired` 更偏 Spring 原生体系，默认按类型注入；`@Resource` 是标准注解，常被理解为按名称注入。两者都能完成依赖注入，但在 Spring 项目里我更常见的是 `@Autowired`，如果需要强调名称匹配或者团队规范要求，也可能用 `@Resource`。 

## 6. 配置相关注解怎么讲

### `@Configuration`

> `@Configuration` 用来标记配置类，Spring 启动时会把这个类当作配置来源之一。

### `@Bean`

> `@Bean` 一般写在配置类的方法上，表示把该方法返回的对象注册成容器里的 Bean。

### `@Component` 和 `@Bean` 区别怎么答

> `@Component` 更适合标在自己写的业务类上，让 Spring 扫描注册；`@Bean` 更适合在配置类中手动注册对象，尤其是第三方组件或者需要显式定制初始化逻辑的对象。

### `@Value`

> `@Value` 适合读取单个配置项。

### `@ConfigurationProperties`

> `@ConfigurationProperties` 更适合把一组相关配置批量绑定到一个配置对象上，比多个 `@Value` 更清晰，也更适合维护。

## 7. Web 层常见注解怎么讲

### `@RequestMapping`

> `@RequestMapping` 用来做请求路径映射，可以标在类上，也可以标在方法上。

### `@GetMapping` / `@PostMapping`

> 它们本质上是 `@RequestMapping` 的语义化变体，用来明确区分不同 HTTP 请求方式。

### `@RequestBody`

> `@RequestBody` 用来接收请求体里的 JSON 数据，并把它转换成 Java 对象。

### `@RequestParam`

> `@RequestParam` 一般用于接收查询参数或者表单参数。

### `@PathVariable`

> `@PathVariable` 用来接收 URL 路径里的占位参数。

### `@ResponseBody`

> `@ResponseBody` 表示把方法返回值直接写到响应体里，而不是去解析页面视图。

### `@RequestBody` 和 `@RequestParam` 区别怎么答

> `@RequestBody` 取的是请求体里的数据，通常用于接收 JSON；`@RequestParam` 取的是 URL 查询参数或者表单参数。复杂对象提交通常更常见用 `@RequestBody`，简单条件查询更常见用 `@RequestParam`。 

### `@ResponseBody` 和 `@RestController` 区别怎么答

> `@ResponseBody` 一般标在方法上，表示该方法直接返回响应体；`@RestController` 一般标在类上，相当于统一给这个类的方法加上了 `@ResponseBody`。 

## 8. 事务、校验和异常增强类注解怎么讲

### `@Transactional`

> `@Transactional` 用来声明事务，通常放在 `Service` 层控制事务边界。

### `@Valid` 和 `@Validated`

> 这两个注解通常用于参数校验。`@Valid` 是标准校验注解，`@Validated` 是 Spring 的增强版，支持分组校验，所以项目里更常见 `@Validated`。

### `@ControllerAdvice` 和 `@ExceptionHandler`

> `@ControllerAdvice` 一般做全局增强，`@ExceptionHandler` 用来捕获指定异常，两者经常配合起来做统一异常处理和统一返回体封装。

## 9. 启动和扫描类注解怎么讲

### `@ComponentScan`

> `@ComponentScan` 用来指定 Spring 扫描哪些包，把这些包下的组件注册到容器里。

### `@MapperScan`

> `@MapperScan` 一般用于 MyBatis，作用是批量扫描 Mapper 接口并注册成 Bean。

### `@SpringBootApplication`

> `@SpringBootApplication` 是 Spring Boot 启动类上的核心组合注解，可以理解成把配置声明、自动装配和组件扫描组合到了一起。

## 10. 自定义注解怎么顺手讲

如果面试官问：

> 你项目里有没有自定义注解？

可以这样答：

> 自定义注解本身只是一个标记，真正生效通常还要配合 AOP、拦截器或者参数解析器来实现。像操作日志、权限校验、幂等控制、埋点统计，这些场景都适合通过自定义注解配合切面来做。 

## 11. 面试里最值得优先背的 8 题

1. `@Autowired` 和 `@Resource` 区别
2. `@Component` 和 `@Bean` 区别
3. `@Controller` 和 `@RestController` 区别
4. `@RequestBody` 和 `@RequestParam` 区别
5. `@ResponseBody` 和 `@RestController` 关系
6. `@Transactional` 为什么一般放在 `Service` 层
7. `@Valid` 和 `@Validated` 区别
8. `@SpringBootApplication` 大概由哪些能力组成

## 12. 最容易答错的点

- 只会罗列注解，不会分类
- 不结合项目场景，听起来像死背
- 知道注解名字，但说不清它解决什么问题
- 把 `@Component` 和 `@Bean` 混为一谈
- 把 `@ResponseBody` 和 `@RestController` 说成完全一样但说不清层级差异

## 13. 一句话收尾

> Spring 注解这条线真正要准备的，不是把注解名背得越多越好，而是能把它们按职责分类，并讲清楚各自在项目里是怎么落地的。
