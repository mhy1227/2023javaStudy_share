# Spring 高频追问：常见注解与面试回答

## 1. 这份文档是干什么的
这份文档专门补 Spring 面试里很常见的一类追问：

1. Spring 这边除了 IOC、AOP、事务，还会继续问什么
2. 你项目里常用过哪些 Spring 注解
3. 这些注解分别是做什么的
4. 面试官会不会顺着注解继续追问
5. 怎么把“我用过这些注解”讲得不像背八股

这类问题很高频，而且经常是顺着你的项目经历往下问的。

比如面试官可能这样问：

- 你项目里 Spring 用得多吗
- 你常用哪些 Spring 注解
- `@Autowired` 和 `@Resource` 有什么区别
- `@Component`、`@Service`、`@Repository` 有什么区别
- `@RestController` 和 `@Controller` 有什么区别
- `@Transactional` 你怎么用的，为什么会失效
- `@Configuration` 和 `@Bean` 是干什么的
- 你们项目有没有自定义配置类
- `@Value` 和 `@ConfigurationProperties` 有什么区别
- `@ResponseBody` 是干什么的
- `@SpringBootApplication`、`@ComponentScan`、`@MapperScan` 这些你怎么理解
- `@Validated`、`@Valid` 有没有用过
- `@Async`、`@Scheduled` 有没有用过
- 你项目里有没有自定义注解

所以这份非常值得单独准备。

---

## 2. 先记一个总回答骨架
如果面试官问：

> 你在 Spring 里常用过哪些注解？

你可以先用这版总回答：

> 我项目里常用的 Spring 注解主要分几类。第一类是组件注册类，比如 `@Component`、`@Service`、`@Repository`、`@Controller`、`@RestController`；第二类是依赖注入类，比如 `@Autowired`、`@Resource`；第三类是配置相关，比如 `@Configuration`、`@Bean`、`@Value`、`@ConfigurationProperties`；第四类是 Web 层接口相关，比如 `@RequestMapping`、`@GetMapping`、`@PostMapping`、`@RequestBody`、`@ResponseBody`、`@PathVariable`、`@RequestParam`；第五类是事务和增强相关，比如 `@Transactional`、`@Validated`、`@ExceptionHandler`；第六类是启动和扫描相关，比如 `@SpringBootApplication`、`@ComponentScan`、`@MapperScan`。如果结合我自己的项目，最常用的还是 `@Service`、`@RestController`、`@Autowired`、`@RequestBody`、`@Transactional` 这几类。`

这段话的作用不是把所有注解都背出来，而是先把面试节奏控住，让对方知道你不是只会零散记忆。

---

## 3. 面试官还可能问什么
Spring 这边，除了主线问题，常见追问还有这些：

- 你项目里 Bean 是怎么交给 Spring 管理的
- `@Component` 和 `@Bean` 的区别是什么
- 依赖注入有哪几种方式
- 为什么更推荐构造器注入
- `@Autowired` 注入失败的原因有哪些
- `@Transactional` 为什么会失效
- Spring 事务为什么默认只回滚运行时异常
- `@RequestBody` 和 `@RequestParam` 有什么区别
- `@ResponseBody` 和 `@RestController` 有什么关系
- `@ControllerAdvice` 你有没有用过
- `@ExceptionHandler` 是怎么做全局异常处理的
- `@ConfigurationProperties` 为什么比多个 `@Value` 更适合配置项
- Spring Boot 启动类上的 `@SpringBootApplication` 包含什么
- `@ComponentScan` 扫描范围怎么定
- `@MapperScan` 是干什么的
- `@Valid` 和 `@Validated` 有什么区别
- 如果让你做一个自定义注解，你会怎么做

所以你可以把它理解成三层：

1. Spring 核心能力
2. 注解如何使用
3. 注解背后的原理和常见坑

---

## 4. 组件注册类注解怎么讲

### 4.1 `@Component`
标准回答：

> `@Component` 是一个通用组件注解，表示把当前类交给 Spring 容器管理。

继续展开：

> 它本质上是最基础的组件标记，很多更语义化的注解其实都是它的派生，比如 `@Service`、`@Repository`、`@Controller`。

---

### 4.2 `@Service`
标准回答：

> `@Service` 一般放在业务层，用来标记这是一个 Service Bean。它功能上和 `@Component` 类似，但语义更清晰，便于分层管理和阅读代码。

项目口语化说法：

> 像我项目里课程模块、试题模块、AI 批阅模块的核心业务逻辑，基本都会放在 `@Service` 标注的类里。

---

### 4.3 `@Repository`
标准回答：

> `@Repository` 一般用于数据访问层，语义上表示这是持久层组件。

顺手补一句：

> 在一些场景下它还有数据访问异常转换的语义，不过很多项目里如果是 MyBatis Mapper 接口，更多是直接交给 Mapper 扫描去管理。

---

### 4.4 `@Controller` 和 `@RestController`
标准回答：

> `@Controller` 主要用于传统 MVC 场景，通常返回页面视图；`@RestController` 更适合前后端分离项目，它相当于 `@Controller + @ResponseBody`，返回的通常是 JSON 数据。

如果面试官问你项目里用哪个：

> 我做的是前后端分离项目，所以接口层主要用的是 `@RestController`。

---

## 5. 依赖注入类注解怎么讲

### 5.1 `@Autowired`
标准回答：

> `@Autowired` 是 Spring 常用的自动注入注解，默认按类型注入。

顺着讲两句更像真实使用：

> 一般可以标在字段、构造器、Setter 上。现在更推荐构造器注入，因为依赖关系更明确，也更方便测试。

---

### 5.2 `@Resource`
标准回答：

> `@Resource` 是 JSR 标准里的注解，默认更偏向按名称注入，如果按名称找不到，再看具体实现和配置。

常见回答差异版：

> 简单理解的话，`@Autowired` 更偏 Spring 自己的体系，默认按类型；`@Resource` 更偏标准注解，常被理解为默认按名称。

---

### 5.3 `@Autowired` 和 `@Resource` 区别怎么答
可直接背的版本：

> 我一般会这样理解：`@Autowired` 是 Spring 原生注解，默认按类型注入；`@Resource` 是 Java 标准注解，通常按名称注入。从项目实践看，两者都能完成依赖注入，但如果是 Spring 体系里，我更常见的是 `@Autowired`，如果要强调名称匹配或者团队规范要求，也会用 `@Resource`。

如果再被追问“现在更推荐什么注入方式”：

> 比起字段注入，我更倾向构造器注入，因为依赖是显式的，也更利于单测和不可变设计。

---

## 6. 配置相关注解怎么讲

### 6.1 `@Configuration`
标准回答：

> `@Configuration` 用来标记当前类是一个配置类，Spring 启动时会把这个类当作配置来源之一。

项目化说法：

> 比如数据库配置、线程池配置、Redis 配置、拦截器配置，这类一般都会放到 `@Configuration` 类里。

---

### 6.2 `@Bean`
标准回答：

> `@Bean` 一般写在配置类的方法上，表示把该方法返回的对象注册成 Spring 容器中的 Bean。

高频追问：

> `@Component` 是直接标在类上让 Spring 扫描注册，`@Bean` 是在配置类里通过方法显式注册对象。前者适合自己写的业务类，后者适合第三方组件或者需要手动定制初始化逻辑的对象。

---

### 6.3 `@Value`
标准回答：

> `@Value` 用来读取配置文件中的单个配置项，比如读取超时时间、开关、URL 等。

---

### 6.4 `@ConfigurationProperties`
标准回答：

> `@ConfigurationProperties` 适合把一组相关配置批量绑定到一个配置对象上，比多个 `@Value` 更清晰，也更适合维护。

面试可直接答的对比：

> 如果只是取一个简单配置，用 `@Value` 很方便；如果是一整组配置，比如 AI 模型参数、文件存储配置、Redis 集群配置，那我会更倾向 `@ConfigurationProperties`，因为结构更清晰，也更适合统一管理。

---

## 7. Web 层常见注解怎么讲

### 7.1 `@RequestMapping`
标准回答：

> `@RequestMapping` 用来做请求路径映射，可以标在类上也可以标在方法上。

---

### 7.2 `@GetMapping`、`@PostMapping`
标准回答：

> 它们本质上是 `@RequestMapping` 的语义化变体，用来明确区分 GET、POST 这类请求方式，可读性更好。

---

### 7.3 `@RequestBody`
标准回答：

> `@RequestBody` 用来接收请求体里的 JSON 数据，并把它转换成 Java 对象。

项目口语化说法：

> 前后端分离项目里，新增、修改、批量操作这种接口非常常见，所以 `@RequestBody` 基本是高频使用。

---

### 7.3.1 `@ResponseBody`
标准回答：

> `@ResponseBody` 的作用是把方法返回值直接写到 HTTP 响应体里，而不是去解析成页面视图。前后端分离项目里通常返回 JSON，所以这个注解很常见。

高频追问怎么接：

> `@RestController` 本质上就可以理解成 `@Controller + @ResponseBody`，所以如果类上已经用了 `@RestController`，通常就不需要在每个方法上再单独写 `@ResponseBody` 了。

---

### 7.4 `@RequestParam`
标准回答：

> `@RequestParam` 一般用来接收查询参数或者表单参数。

---

### 7.5 `@PathVariable`
标准回答：

> `@PathVariable` 用来接收 URL 路径里的占位参数，比如 `/user/{id}` 里的 `id`。

---

### 7.6 `@RequestBody` 和 `@RequestParam` 区别怎么答
可以直接背：

> `@RequestBody` 取的是请求体里的数据，通常用于接收 JSON；`@RequestParam` 取的是 URL 查询参数或者表单参数。前后端分离项目里，复杂对象提交通常用 `@RequestBody`，简单条件查询更常见的是 `@RequestParam`。

---

### 7.7 `@ResponseBody` 和 `@RestController` 区别怎么答
可以直接背：

> `@ResponseBody` 一般是标在方法上，表示该方法直接返回响应体内容；`@RestController` 一般标在类上，相当于给这个类里的方法统一加上了 `@ResponseBody`。所以前后端分离项目里，我更常用 `@RestController`，这样写起来更直接。

---

## 8. 校验与异常增强类注解怎么讲

### 8.1 `@Valid` 和 `@Validated`
标准回答：

> 这两个注解一般用于参数校验。`@Valid` 是标准校验注解，`@Validated` 是 Spring 提供的增强版，支持分组校验，所以项目里更常见的是 `@Validated`。

项目化说法：

> 比如新增和修改参数规则不一样，或者接口入参对象上有必填、长度、格式校验时，就会配合 `@Validated` 使用。

---

### 8.2 `@ControllerAdvice` 和 `@ExceptionHandler`
标准回答：

> `@ControllerAdvice` 一般做全局增强，`@ExceptionHandler` 用来捕获指定异常，两者经常结合起来做统一异常处理和统一返回体封装。

口语化一点：

> 如果项目里不想每个接口都自己 try-catch，一般就会用这套方案统一接住异常，然后返回统一错误码和错误信息。

---

## 9. 启动、扫描与集成类注解怎么讲

### 9.1 `@ComponentScan`
标准回答：

> `@ComponentScan` 用来指定 Spring 要扫描哪些包，把这些包下的组件类注册到容器里。

面试官继续问时可以这样接：

> 默认情况下，Spring Boot 会从启动类所在包往下扫描，所以一般会把启动类放在比较上层的根包位置。如果包结构比较特殊，才会显式指定扫描路径。

---

### 9.2 `@MapperScan`
标准回答：

> `@MapperScan` 一般用于 MyBatis，作用是批量扫描 Mapper 接口并注册成 Bean，避免每个 Mapper 都单独配置。

---

### 9.3 `@SpringBootApplication`
标准回答：

> `@SpringBootApplication` 是启动入口上的核心组合注解，一般可以理解成包含了配置类声明、自动装配和组件扫描三部分能力。

---

## 10. 异步、定时与扩展能力注解也可能会问

### 10.1 `@Async`
标准回答：

> `@Async` 用来标记异步方法，让方法调用可以异步执行，通常会配合线程池使用。

面试可补一句：

> 不过它本质上也是基于代理生效的，所以自调用场景下同样要注意失效问题。

---

### 10.2 `@Scheduled`
标准回答：

> `@Scheduled` 用来声明定时任务，比如固定时间执行、固定间隔执行、Cron 表达式执行。

项目口语化：

> 如果项目里有定时同步、定时清理、定时统计这类需求，这个注解很常见。

---

## 11. 自定义注解怎么讲

这个问题其实很像“你有没有真正做过项目扩展”。

如果面试官问：

> 你项目里有没有自定义注解？

你可以这样答：

> 如果项目里有一些横切需求，比如操作日志、权限校验、幂等控制、数据范围控制、接口防重复提交、统一埋点，这些都可以通过自定义注解去做。我理解自定义注解本身只是一个标记，真正生效通常还需要配合 AOP、拦截器或者参数解析器来实现。

这是很关键的一句，因为它能体现你知道“注解不是魔法，背后要有处理逻辑”。

---

### 11.1 自定义注解的一般实现思路
可以直接背：

> 我会先定义一个注解，明确它的作用目标、保留策略和需要的属性；然后再通过 AOP 或者拦截器去拦截带这个注解的方法或类，读取注解里的参数，再执行对应逻辑。比如做操作日志，就可以在切面里拿到方法名、参数、用户信息和执行结果，最后落库。

---

### 11.2 如果被继续追问“你做过没有”
如果你做过，就按真实项目答。

如果你没做过，也可以稳一点这样说：

> 我项目里直接写自定义注解的场景不算特别多，但我知道它的落地思路，本质上就是注解做标记，AOP 或拦截器去识别和处理。像日志、权限、幂等这类场景都很适合这么做。

这样比硬说“做过很多”安全得多。

---

## 12. 一段更完整、像真实面试的回答

如果面试官问：

> 你项目里 Spring 常用哪些注解？

你可以升级成这版：

> 我项目里常用的 Spring 注解主要分几类。第一类是组件注册类，比如 `@Service`、`@Repository`、`@RestController`，主要对应业务层、持久层和接口层 Bean 的管理；第二类是依赖注入类，比如 `@Autowired`、`@Resource`；第三类是 Web 层接口类，比如 `@RequestMapping`、`@PostMapping`、`@RequestBody`、`@RequestParam`、`@PathVariable`，如果是前后端分离项目，还会涉及 `@ResponseBody`，不过很多时候直接用 `@RestController` 就统一处理了；第四类是配置相关，比如 `@Configuration`、`@Bean`、`@Value`、`@ConfigurationProperties`；第五类是事务和增强相关，比如 `@Transactional`、`@Validated`、`@ControllerAdvice`、`@ExceptionHandler`；另外启动类上还会有 `@SpringBootApplication`，MyBatis 整合时也常见 `@MapperScan`。如果结合我自己的项目，最常用的是 `@Service`、`@RestController`、`@Autowired`、`@RequestBody`、`@Transactional`，如果再往外扩一点，就是统一异常处理和参数校验这块。`

---

## 13. 你现在最该优先背的注解题

优先级最高的一批是：

1. `@Autowired` 和 `@Resource` 区别
2. `@Component` 和 `@Bean` 区别
3. `@Controller`、`@ResponseBody`、`@RestController` 关系
4. `@RequestBody` 和 `@RequestParam` 区别
5. `@Transactional` 为什么会失效
6. `@SpringBootApplication` 由哪些注解组成
7. `@Valid` 和 `@Validated` 区别
8. 自定义注解一般怎么实现

---

## 14. 最后给你一个更全的速记版

你至少把下面这些记住：

1. `@RestController = @Controller + @ResponseBody`
2. `@Autowired` 默认按类型注入，`@Resource` 常被理解为按名称注入
3. `@Component` 是通用组件，`@Service`、`@Repository`、`@Controller` 是更语义化的派生
4. `@Bean` 是在配置类里显式注册对象，常用于第三方组件
5. `@RequestBody` 接请求体 JSON，`@RequestParam` 接查询参数或表单参数
6. `@Validated` 比 `@Valid` 更常见，因为它支持分组校验
7. `@ControllerAdvice + @ExceptionHandler` 常用于统一异常处理
8. `@ComponentScan` 扫 Spring 组件，`@MapperScan` 扫 MyBatis Mapper
9. `@Async` 做异步，`@Scheduled` 做定时任务
10. 自定义注解本身只是标记，真正生效通常靠 AOP、拦截器或参数解析器

## 15. 事务相关注解怎么讲

### 15.1 `@Transactional`
标准回答：

> `@Transactional` 用来声明事务。它能让方法中的多个数据库操作放在同一个事务里，要么一起成功，要么一起回滚。

项目化表达：

> 比如订单、支付、库存、作答记录、试卷结果汇总这类涉及多表写入的场景，通常就要考虑事务边界。

---

### 15.2 面试官顺着会问什么
`@Transactional` 往往不是一句话就结束，后面常见追问有：

- 事务加在什么地方更合适
- 为什么 `@Transactional` 会失效
- 默认回滚哪些异常
- 事务传播行为了解吗
- 事务隔离级别了解吗

你可以先稳住一句：

> 事务我一般加在 Service 层，因为事务边界更适合放在业务层统一控制。

---

## 16. 异常处理相关注解也可能会问

### 16.1 `@ControllerAdvice`
标准回答：

> `@ControllerAdvice` 一般用来做全局增强，比如统一异常处理、统一数据绑定、统一返回处理等。

---

### 16.2 `@ExceptionHandler`
标准回答：

> `@ExceptionHandler` 一般配合 `@ControllerAdvice` 使用，用来捕获指定类型的异常并统一返回错误信息。

项目口语化说法：

> 如果项目里需要统一返回错误码、错误信息、异常提示，这两个注解就很常见。

---

## 17. `@SpringBootApplication` 也很容易被问
可直接背：

> `@SpringBootApplication` 是 Spring Boot 启动类上的核心注解，它本身是一个组合注解，一般可以理解成包含了 `@SpringBootConfiguration`、`@EnableAutoConfiguration`、`@ComponentScan`，也就是配置类声明、开启自动装配、组件扫描这三部分能力。

这个问题经常是从“你项目怎么启动”顺着问下来的。

---

## 18. 一段更像真实面试的完整回答
如果面试官问：

> 你项目里 Spring 常用哪些注解？

你可以这样答：

> 我项目里比较常用的 Spring 注解主要有几类。第一类是组件注册类，比如 `@Service`、`@RestController`、`@Component`，这个主要对应业务层和接口层 Bean 的管理。第二类是依赖注入，比如 `@Autowired`、`@Resource`，用来完成对象之间的协作。第三类是 Web 层注解，比如 `@RequestMapping`、`@PostMapping`、`@RequestBody`、`@RequestParam`，主要用于接口请求的映射和参数接收。第四类是配置相关，比如 `@Configuration`、`@Bean`、`@Value`、`@ConfigurationProperties`，这个主要用于项目配置和第三方组件整合。还有一类是事务相关的 `@Transactional`，一般会用在 Service 层控制事务边界。结合我的项目，最常用的其实还是 `@Service`、`@RestController`、`@RequestBody`、`@Autowired` 和 `@Transactional` 这些。`

这段比“我用过很多注解，比如……”更像真正做过项目的人。

---

## 19. 面试时不要这样答
下面这种答法不太好：

> 我用过 `@Service`、`@Controller`、`@Autowired`、`@RequestBody`、`@Transactional`……

问题在于：

1. 只有罗列，没有分类
2. 没有结合项目
3. 面试官一听就会继续往深里追
4. 自己反而容易乱

更好的方式是：

1. 先分类
2. 再挑项目里最常用的说
3. 最后等对方追问某一个注解时再展开

---

## 20. 最后给你一个速记版
你至少把下面这几句记住：

1. `@Service`、`@Repository`、`@Controller`、`@RestController` 本质上都属于组件注册，只是语义不同。
2. `@Autowired` 默认按类型注入，`@Resource` 常被理解为按名称注入。
3. `@Configuration` 是配置类，`@Bean` 是把方法返回对象注册进容器。
4. `@RequestBody` 接 JSON 请求体，`@RequestParam` 接查询参数或表单参数。
5. `@Transactional` 一般放在 Service 层，用来控制事务边界。
6. `@ConfigurationProperties` 适合批量绑定配置，比多个 `@Value` 更清晰。
7. `@RestController` 更适合前后端分离项目。
8. `@SpringBootApplication` 是启动入口上的核心组合注解。

---

## 21. 你现在最该准备的追问
如果你准备 Spring 面试，我建议你下一步重点背这几题：

1. `@Autowired` 和 `@Resource` 区别
2. `@Component` 和 `@Bean` 区别
3. `@Controller` 和 `@RestController` 区别
4. `@RequestBody` 和 `@RequestParam` 区别
5. `@Transactional` 为什么会失效
6. `@SpringBootApplication` 由哪些注解组成

这 6 个问题，命中率非常高。
