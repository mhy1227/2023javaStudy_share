# Spring MVC 笔记

## 1. 这份文档怎么用

这一篇专门补 Spring 在 Web 层的主线：

- 什么是 Spring MVC
- 一次请求进来之后大概怎么走
- `DispatcherServlet` 是干什么的
- `HandlerMapping`、`HandlerAdapter` 分别负责什么
- Controller 返回视图或 JSON 时分别怎么处理

如果你前面已经补过 IOC、AOP、事务，这一篇就是把“请求为什么能走到 Controller”这条线接起来。

## 2. 先记住最核心的 6 句

1. Spring MVC 是 Spring 提供的 Web 层开发框架。
2. 一次请求通常先进入 `DispatcherServlet`。
3. `DispatcherServlet` 是整个请求分发流程的核心入口，也叫前端控制器。
4. `HandlerMapping` 负责找到该由谁处理请求。
5. `HandlerAdapter` 负责按 Spring MVC 约定真正调用目标处理器。
6. Controller 返回结果后，Spring MVC 还会继续做视图解析或消息转换。

## 3. 什么是 Spring MVC

最稳的回答：

> Spring MVC 是 Spring 提供的 Web 层框架，主要负责把请求接收、参数绑定、业务调用和结果返回这一整套流程组织起来。

更口语一点：

> 你可以把它理解成 Spring 在接口层和页面层的一套标准请求处理方案。

## 4. MVC 怎么简单理解

如果面试官顺带问 MVC，可以这样答：

- `Model`：数据和业务结果
- `View`：页面展示
- `Controller`：请求接收和流程控制

如果是前后端分离项目，可以顺手补一句：

> 现在很多项目不一定返回传统页面，而是更常返回 JSON，但请求分发这套思路本质上还是 MVC 这一层在组织。

## 5. Spring MVC 执行流程怎么答

先记主干流程：

1. 请求先进入 `DispatcherServlet`
2. `DispatcherServlet` 通过 `HandlerMapping` 找到对应处理器
3. 再通过 `HandlerAdapter` 调用目标 Controller 方法
4. Controller 执行业务逻辑并返回结果
5. Spring MVC 再根据返回值类型做后续处理
6. 最终返回页面或 JSON 给客户端

这 6 步已经够你先把主线答出来。

## 6. `DispatcherServlet` 是什么

这是高频题。

标准回答：

> `DispatcherServlet` 是 Spring MVC 的核心调度入口，也叫前端控制器，它负责统一接收请求并把后续分发流程串起来。

一句话版：

> 所有请求先进总入口，再由总入口统一调度。

## 7. 为什么叫前端控制器

可以这样答：

> 因为它位于整个请求处理链路的前面，负责统一接收和分发请求，相当于把分散的控制逻辑收口到了一个总入口上。

## 8. `HandlerMapping` 是干什么的

标准回答：

> `HandlerMapping` 的核心作用是根据当前请求找到应该由哪个处理器来处理，也就是找到对应的 Controller 方法。

更口语一点：

> 它负责“找人”，看这次请求到底该交给谁。

## 9. `HandlerAdapter` 是干什么的

很多人容易漏掉这题。

可以这样答：

> `HandlerAdapter` 的作用是按照 Spring MVC 约定的方式，真正去调用找到的目标处理器。

一句话版：

> `HandlerMapping` 负责找到，`HandlerAdapter` 负责调起来。

## 10. 参数绑定发生在什么阶段

面试里有时会顺着问。

可以这样答：

> 在 Controller 方法真正执行之前，Spring MVC 会根据请求参数、路径变量、请求体等信息，完成方法参数的绑定和转换。

这题不用讲到非常底层，答到这个粒度就够了。

## 11. Controller 主要负责什么

比较稳的说法：

> Controller 主要负责接收请求、拿到参数、调用 Service 处理业务，然后把结果返回给 Spring MVC。

一句话记忆：

> Controller 更像业务流程入口，而不是业务实现本身。

## 12. Controller 返回之后还发生了什么

这题很适合继续追问。

可以这样答：

> Controller 返回结果后，Spring MVC 会根据返回值类型继续处理。如果是页面场景，就可能走视图解析；如果是前后端分离场景，就更常见走消息转换，把对象转成 JSON 写回响应体。

## 13. 返回视图和返回 JSON 的区别怎么讲

### 返回视图

> Spring MVC 会继续走视图解析器，把逻辑视图名解析成真正的页面资源。

### 返回 JSON

> Spring MVC 会通过消息转换器把对象转成 JSON，然后写回响应体。

一句话版：

> 一个偏页面渲染，一个偏数据输出。

## 14. 一版适合面试的完整回答

> Spring MVC 是 Spring 提供的 Web 层开发框架。一次请求通常先进入 `DispatcherServlet`，它作为前端控制器统一接收请求，然后通过 `HandlerMapping` 找到对应处理器，再通过 `HandlerAdapter` 真正调用目标 Controller 方法。Controller 执行业务逻辑后返回结果，Spring MVC 会继续根据返回值类型处理，如果是页面场景就走视图解析，如果是前后端分离场景就通过消息转换器把对象转成 JSON，最后再把结果返回给客户端。 

## 15. 最容易答错的点

- 只会背 `DispatcherServlet`，但说不清它和其他组件怎么配合
- 不知道 `HandlerMapping` 和 `HandlerAdapter` 的职责差异
- 以为 Controller 返回以后流程就结束了
- 把 Spring MVC 和前后端分离完全对立起来
- 只记概念，不会讲请求是怎么流动的

## 16. 一句话收尾

> Spring MVC 这条线真正要讲顺的，不只是几个组件名，而是一次请求为什么能被统一接住、找到处理器、调起业务，再转换成最终响应。
