# 牛客 Spring 高频面经归纳

## 1. 这份文档是干什么的
这份文档不是讲教材，而是把牛客上真实面经里经常出现的 Spring 相关问题做一次归纳。

目的很明确：

1. 看真实一面到底爱问什么
2. 判断哪些点是高频，哪些点只是补充
3. 给后面的背诵和模拟面试排优先级

---

## 2. 先说结论
如果只看牛客上的 Spring 面经，真实面试里最常见的不是单独背注解，而是一条链路式追问：

1. Spring 核心：IOC、AOP、Bean 生命周期、循环依赖
2. Spring MVC：请求怎么进来，怎么到 Controller，参数怎么绑定
3. Spring Boot：为什么更方便，自动装配怎么做，starter 是什么
4. 事务：`@Transactional` 怎么实现，为什么失效，默认回滚什么异常
5. 注解：`@Autowired`、`@Resource`、`@Bean`、`@Component`、`@RestController`
6. 项目结合：你项目里用到了哪些 Spring 能力，为什么这样设计

所以你要记住一句：

> 注解会问，但一般不是终点，面试官更喜欢顺着注解继续往事务、MVC、Boot、AOP、项目设计里追。

---

## 3. 牛客面经里反复出现的高频点

### 3.1 第一档高频
这是命中率最高的一批：

1. Spring Boot 自动装配
2. `@Transactional` 原理与失效场景
3. `@Autowired` 和 `@Resource` 区别
4. `@Bean` 和 `@Component` 区别
5. `@Controller`、`@ResponseBody`、`@RestController` 关系
6. Bean 生命周期
7. 循环依赖
8. 拦截器和过滤器区别

这批问题的特点是：

1. 既能问基础
2. 也能顺着问原理
3. 还能接项目场景

---

### 3.2 第二档高频
这一批略低一点，但在一面和二面也很常见：

1. Spring MVC 执行流程
2. `@RequestBody` 和 `@RequestParam` 区别
3. `@Valid` 和 `@Validated` 区别
4. `@ComponentScan` 和 `@MapperScan`
5. AOP 的底层原理
6. 自定义注解怎么实现
7. `@Configuration` 和 `@Bean`
8. 统一异常处理怎么做

---

### 3.3 第三档补充
这些不一定每场都问，但如果对方追细节，很容易碰到：

1. Spring Boot 的 SPI
2. starter 的作用
3. 条件装配注解
4. `@Async` 和 `@Scheduled`
5. 参数绑定和消息转换器
6. `@ConfigurationProperties` 和 `@Value`

---

## 4. 牛客面经透露出的真实问法
从牛客的帖子看，Spring 面试常见有四种问法。

### 4.1 直接问概念
比如：

- 什么是 IOC
- 什么是 AOP
- 什么是自动装配
- 什么是事务

这种题一般是入口题。

---

### 4.2 问注解区别
比如：

- `@Autowired` 和 `@Resource`
- `@Bean` 和 `@Component`
- `@RequestBody` 和 `@RequestParam`
- `@Controller` 和 `@RestController`

这种题看起来是八股，但实际上面试官想看的是：

1. 你有没有真正写过接口
2. 你有没有真正配过 Spring
3. 你是不是只会背定义

---

### 4.3 顺着原理追问
比如：

- `@Transactional` 为什么会失效
- Spring 事务底层怎么实现
- Bean 生命周期有哪些阶段
- 循环依赖为什么能解决，什么时候不能解决
- 自动装配怎么把配置类装进去

这一类就是区分度题。

---

### 4.4 结合项目问
比如：

- 你项目里用到哪些 Spring 注解
- 你们项目事务加在什么地方
- 统一异常处理怎么做
- 自定义注解做过没有
- 拦截器和过滤器在你项目里怎么用

这类最像真实一面。

---

## 5. 从牛客面经反推，你现在该怎么准备

### 5.1 不要只背注解名
如果你只能说：

> 我用过 `@Service`、`@Autowired`、`@RequestBody`、`@Transactional`

这不够。

你至少要能接出：

1. 它干什么
2. 它和谁容易混
3. 它在项目里为什么要这么用
4. 它背后的常见坑是什么

---

### 5.2 Spring 最容易被追成一条线
一条很常见的真实追问链路是：

1. 你项目里常用哪些 Spring 注解
2. `@Autowired` 和 `@Resource` 区别
3. `@Transactional` 你怎么用
4. 为什么会失效
5. Spring 事务底层怎么实现
6. 你们异常怎么统一处理
7. Spring Boot 自动装配原理

所以你准备的时候也不要拆得太散。

---

## 6. 你现在最该优先补的 10 题
按牛客真实面经频率和面试链路，我建议你先准备这 10 题：

1. 什么是 IOC，什么是 AOP
2. Bean 生命周期
3. `@Autowired` 和 `@Resource` 区别
4. `@Bean` 和 `@Component` 区别
5. `@Controller`、`@ResponseBody`、`@RestController` 关系
6. `@Transactional` 原理和失效场景
7. Spring MVC 执行流程
8. Spring Boot 自动装配原理
9. 拦截器和过滤器区别
10. 自定义注解怎么落到 AOP 上

这 10 题基本能覆盖大多数 Spring 一面。

---

## 7. 哪些题你已经补到了，哪些还值得补

### 7.1 已经补得比较完整的
你当前这套资料里已经覆盖得不错的有：

1. Spring 核心
2. `@Transactional` 和失效场景
3. Spring MVC
4. Spring Boot 与自动装配
5. 常见注解

---

### 7.2 还值得补一层模拟问答的
现在更值得继续补的是：

1. Bean 生命周期和循环依赖
2. 拦截器和过滤器区别
3. AOP 和自定义注解结合
4. 自动装配追问版
5. Spring 高频一问一答模拟

---

## 8. 推荐背诵顺序
如果你现在脑子很乱，不要全背，按这个顺序来：

1. 常见注解总回答
2. `@Autowired` 和 `@Resource`
3. `@Transactional`
4. `@RestController` 和 `@ResponseBody`
5. Spring MVC 执行流程
6. Spring Boot 自动装配
7. Bean 生命周期
8. 拦截器和过滤器

---

## 9. 牛客来源样本
下面这些帖子能支撑上面的判断：

1. Spring 高频总结帖：强调 `@Autowired/@Resource`、`@Bean/@Component`、Bean 生命周期、循环依赖、事务实现  
   https://www.nowcoder.com/discuss/353159266464899072
2. 2025 Java 一面：明确问 Spring Boot 自动装配、SPI、拦截器和过滤器区别、Spring 事务实现原理  
   https://www.nowcoder.com/feed/main/detail/a03778b03a0242f49aac7ceb0bc7f690
3. Java 一面项目深挖：明确问事务注解内部实现、异常处理、Spring 源码理解  
   https://www.nowcoder.com/feed/main/detail/26a5eb4da5564897ab8f911184c49657
4. 面经中直接问“用了哪些 Spring 组件、用了哪些注解、Bean 生命周期”  
   https://www.nowcoder.com/feed/main/detail/f6fc5bf8573844999b028abf608ff500?sourceSSR=enterprise
5. 二面面经里继续问 Spring Boot 自动装配原理  
   https://www.nowcoder.com/discuss/850635369014931456
6. 面经里明确出现“知道自定义注解的原理吗”  
   https://www.nowcoder.com/feed/main/detail/f0c6c767a2794b8bbb71d2ff15af1257

---

## 10. 最后一句话结论
如果只看牛客上的真实面经，Spring 这块最值得准备的不是“多背几个注解”，而是：

> 把注解、事务、MVC、Boot、AOP、项目场景串成一条回答链路。
