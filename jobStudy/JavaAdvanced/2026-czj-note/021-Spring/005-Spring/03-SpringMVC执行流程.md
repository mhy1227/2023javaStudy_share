# Spring MVC 执行流程

## 1. 这份文档是干什么的
这份文档主要解决 Spring MVC 相关的高频问题：

1. 什么是 Spring MVC
2. 一次请求进来之后大概怎么走
3. `DispatcherServlet` 是干什么的
4. `HandlerMapping`、`HandlerAdapter` 是干什么的
5. Controller 返回视图或 JSON 时分别怎么处理

这组题在 Java 后端一面里也很常见。

因为面试官通常会这样追：

- Spring MVC 是什么
- 请求是怎么进入 Controller 的
- `DispatcherServlet` 是做什么的
- 为什么它叫前端控制器
- Controller 返回值之后又怎么处理

所以这一份也很值得单独整理。

---

## 2. 先说最重要的结论
你先记住这四句：

1. **Spring MVC 是 Spring 提供的 Web MVC 框架。**
2. **`DispatcherServlet` 是整个请求分发流程的核心入口。**
3. **`HandlerMapping` 负责找处理器，`HandlerAdapter` 负责真正调用处理器。**
4. **Controller 返回结果后，Spring MVC 还会继续做视图解析或者消息转换。**

这四句基本就是整个流程的骨架。

---

## 3. 什么是 Spring MVC
最稳的回答：

> Spring MVC 是 Spring 提供的 Web 层开发框架，基于 MVC 思想，把请求分发、参数绑定、业务调用、结果返回这些流程组织起来。

更口语一点：

> 你可以把 Spring MVC 理解成 Spring 在 Web 请求处理这一层的标准解决方案。

---

## 4. 什么是 MVC
这题有时也会被顺带问到。

你可以简单说：

- `Model`：数据和业务结果
- `View`：页面展示
- `Controller`：请求分发和流程控制

如果是前后端分离场景，你可以顺手说：

> 现在很多项目更多是返回 JSON，不一定会走传统页面视图，但整体请求分发思想还是 MVC 这套。

---

## 5. Spring MVC 执行流程大概怎么走
这是最核心的一题。

先记基础流程：

1. 请求先到 `DispatcherServlet`
2. `DispatcherServlet` 通过 `HandlerMapping` 找到对应处理器
3. 再通过 `HandlerAdapter` 调用目标 Controller 方法
4. Controller 执行业务逻辑并返回结果
5. Spring MVC 对返回结果做处理
6. 最终返回视图或 JSON 给客户端

这已经够你先答出主干了。

---

## 6. `DispatcherServlet` 是干什么的
这题几乎一定会被问。

你可以这样答：

> `DispatcherServlet` 是 Spring MVC 的核心调度入口，也叫前端控制器。它负责接收请求，然后把整个请求分发流程串起来。

一句话版：

> 所有请求先进总入口，再由总入口统一调度。

---

## 7. 为什么叫“前端控制器”
你可以这样解释：

> 因为它位于整个 Web 请求处理流程的前面，负责统一接收和分发请求，相当于把原本分散的控制逻辑集中到一个总入口上。

---

## 8. `HandlerMapping` 是干什么的
你可以这样答：

> `HandlerMapping` 的作用是根据当前请求找到应该由哪个处理器来处理，也就是找到对应的 Controller 方法。

更口语一点：

> 它负责“找人”，看这次请求该交给谁。

---

## 9. `HandlerAdapter` 是干什么的
这是很多人容易忘的点。

你可以这样说：

> `HandlerAdapter` 的作用是按照 Spring MVC 约定的方式，真正去调用找到的目标处理器。

一句话版：

> `HandlerMapping` 负责找到处理器，`HandlerAdapter` 负责把它调起来。

---

## 10. Controller 做了什么
你可以这样答：

> Controller 负责接收参数、调用 Service 处理业务，并把结果返回给 Spring MVC。

这句很简单，但很实用。

---

## 11. Controller 返回之后 Spring MVC 还做了什么
这题特别适合继续追问。

你可以这样说：

> Controller 返回结果后，Spring MVC 还会根据返回值类型继续处理。如果是页面场景，就可能走视图解析；如果是前后端分离场景，就更常见走消息转换，把对象转成 JSON 返回给客户端。

---

## 12. 返回视图和返回 JSON 的区别怎么讲
你可以这样答：

### 返回视图
> Spring MVC 会继续走视图解析器，把逻辑视图名解析成真正的页面资源。

### 返回 JSON
> Spring MVC 会通过消息转换器把对象转成 JSON，然后写回响应体。

一句话版：

> 一个偏页面渲染，一个偏数据输出。

---

## 13. 参数绑定是在哪一步发生的
这题有时也会被问到。

你可以这样说：

> 参数绑定是在调用 Controller 方法之前，由 Spring MVC 按照请求参数、路径变量、请求体这些信息去完成方法参数封装。

这题不用讲太深，答到这一级就够了。

---

## 14. 一段标准面试回答
如果面试官问你“Spring MVC 执行流程是什么”，你可以直接这样答：

> Spring MVC 的请求一般先进入 `DispatcherServlet`，它作为前端控制器统一接收请求。然后 `DispatcherServlet` 会通过 `HandlerMapping` 找到对应的处理器，再通过 `HandlerAdapter` 真正调用目标 Controller 方法。Controller 执行业务逻辑后返回结果，Spring MVC 再根据返回值类型继续处理，如果是页面场景就走视图解析，如果是前后端分离场景就通过消息转换器把对象转成 JSON，最后再把结果返回给客户端。 

---

## 15. 更口语一点的版本
你也可以这样讲：

> Spring MVC 流程可以简单理解成：请求先到 `DispatcherServlet` 这个总入口，然后它负责找对应的 Controller，再把方法调起来，业务跑完之后再把结果处理成页面或者 JSON 返回。核心就是 `DispatcherServlet` 把整个流程串起来了。 

---

## 16. 最值得先背的 10 句
1. **Spring MVC 是 Spring 提供的 Web 层开发框架。**
2. **`DispatcherServlet` 是整个请求分发流程的核心入口。**
3. **它也叫前端控制器。**
4. **`HandlerMapping` 负责找到处理器。**
5. **`HandlerAdapter` 负责真正调用处理器。**
6. **Controller 负责接参数、调业务、返结果。**
7. **请求处理完后，Spring MVC 还会继续处理返回值。**
8. **返回页面时通常会走视图解析。**
9. **返回对象时通常会走消息转换，转成 JSON。**
10. **Spring MVC 的核心就是把请求分发流程统一串起来。**

---

## 17. 接下来怎么补最顺
到这里为止，Spring 主线已经有三份了：

1. Spring 核心、`IOC`、`AOP`、Bean 生命周期
2. Spring 事务与 `@Transactional` 失效场景
3. Spring MVC 执行流程

如果还继续补，下一份最自然的是：

`04-MyBatis与数据库访问链路.md`

因为面试官问完 MVC，后面很容易继续问到：

> Controller 调到 Service，再到底层数据库访问，这一条链怎么走。
