# Spring Boot 启动流程笔记

## 1. 这份文档怎么用

这一篇专门补一个近年面经里不算少见的追问：

- Spring Boot 启动流程怎么讲
- `SpringApplication.run` 背后大概做了什么
- 启动过程里环境、容器、自动装配、事件大概是怎么串起来的

这题不要求你一上来讲源码，但至少要能把主干流程答顺。

## 2. 先记住最核心的 6 句

1. Spring Boot 启动入口通常是 `SpringApplication.run(...)`。
2. 启动过程不是只创建容器，还会准备环境、推断应用类型、加载配置。
3. 容器创建后会进入 `refresh`，Bean 初始化和自动配置也在这条链上展开。
4. 自动装配不是单独的一步魔法，而是随着容器刷新过程被加载和生效。
5. 启动完成后还会执行 `ApplicationRunner` / `CommandLineRunner`。
6. Spring Boot 启动过程中会发布一系列应用事件。

## 3. 启动入口怎么讲

最常见的起点就是：

```java
SpringApplication.run(MyApplication.class, args);
```

面试里的稳法是：

> Spring Boot 项目通常从 `SpringApplication.run(...)` 进入启动流程，它会负责准备环境、创建并刷新容器，把自动装配、Bean 初始化、事件发布这些流程串起来。

## 4. 启动流程主干怎么记

你可以先记这个高层流程：

1. 进入 `SpringApplication.run(...)`
2. 推断应用类型、准备启动参数和环境
3. 创建 `ApplicationContext`
4. 准备容器并加载 Bean 定义
5. `refresh` 容器
6. 自动装配和 Bean 初始化生效
7. 执行 `ApplicationRunner` / `CommandLineRunner`
8. 应用进入 ready 状态

这一版已经够大多数一面。

## 5. 环境准备在做什么

可以这样答：

> 环境准备阶段主要是在处理配置源、命令行参数、配置文件、Profile 等内容，也就是让后续容器创建和自动装配有一份可用的环境上下文。

一句话记忆：

> 先把配置上下文准备好，后面容器和自动装配才知道该怎么走。

## 6. 创建容器在做什么

可以这样答：

> Spring Boot 会根据应用类型创建合适的 `ApplicationContext`，比如常见的 Servlet Web 场景会走对应的 Web 容器上下文。

这里不需要一上来讲太深实现类，但要知道：

- 不是所有项目都用同一种 `ApplicationContext`
- 应用类型会影响后续容器形态

## 7. `refresh` 为什么关键

这题如果被追问，可以这样答：

> 因为容器真正进入 `refresh` 之后，Bean 创建、依赖注入、后置处理器、自动配置等流程才会系统地跑起来。所以启动流程里最关键的一段，其实就是容器刷新。

## 8. 自动装配在启动流程里的位置怎么理解

可以这样答：

> 自动装配不是孤立发生的，它是随着容器准备和刷新过程被加载进来的。也就是说，Spring Boot 会把符合条件的自动配置类纳入容器，再在刷新过程中让这些配置真正生效。

一句话版：

> 自动装配是启动流程里的一条主线，不是一段独立魔法。

## 9. Runner 在启动后做什么

官方文档里提到，`ApplicationRunner` 和 `CommandLineRunner` 会在应用启动完成前的最后阶段执行。

面试里可以这样答：

> 如果项目里需要在应用启动后执行一些初始化逻辑，可以通过 `ApplicationRunner` 或 `CommandLineRunner` 来做，它们会在 `SpringApplication.run(...)` 完成前被调用。

## 10. 启动事件怎么讲

如果面试官继续往下问，可以这样答：

> Spring Boot 在启动过程中会发布一系列应用事件，例如启动开始、环境准备完成、容器准备完成、启动完成、应用 ready、启动失败等。你不一定要把所有事件名背死，但要知道启动过程不是黑盒，它是有阶段事件的。

根据官方参考文档，事件顺序里常见的有：

- `ApplicationStartingEvent`
- `ApplicationEnvironmentPreparedEvent`
- `ApplicationContextInitializedEvent`
- `ApplicationPreparedEvent`
- `ApplicationStartedEvent`
- `ApplicationReadyEvent`
- `ApplicationFailedEvent`

## 11. 一版适合面试的标准回答

> Spring Boot 启动通常从 `SpringApplication.run(...)` 进入。它不会只做一件事，而是会先准备环境和配置上下文，再根据应用类型创建合适的 `ApplicationContext`，然后准备容器并进入 `refresh` 流程。在容器刷新过程中，Bean 创建、依赖注入、后置处理器和自动装配这条线都会展开。启动后期还会执行 `ApplicationRunner` 或 `CommandLineRunner`，并且整个过程中会发布一系列应用事件，比如环境准备完成、容器准备完成、应用启动完成和 ready 状态等。所以如果要一句话概括，我会说 Spring Boot 启动流程的核心就是“准备环境 -> 创建并刷新容器 -> 让自动装配和 Bean 初始化生效 -> 应用进入 ready 状态”。 

## 12. 最容易答错的点

- 只会说 main 方法和 `run`
- 把自动装配讲成独立的一段黑盒
- 不知道 `refresh` 是启动流程里的关键节点
- 不知道启动后还有 Runner 和事件
- 一上来讲太深源码，反而主干流程讲不顺

## 13. 一句话收尾

> Spring Boot 启动流程题真正要答顺的，不是源码细枝末节，而是知道环境、容器、自动装配和应用 ready 状态是怎么一步步串起来的。
