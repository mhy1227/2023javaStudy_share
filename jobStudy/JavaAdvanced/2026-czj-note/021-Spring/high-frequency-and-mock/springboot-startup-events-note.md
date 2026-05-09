# Spring Boot 启动事件笔记

## 1. 这份文档怎么用

这一篇是 `springboot-startup-flow-note.md` 的补充版，专门把启动过程里的事件单独拎出来。

适合：

- 面试官继续深问启动流程
- 你想把启动流程讲得更完整
- 你需要区分“环境准备好了”、“容器准备好了”、“应用 ready 了”这些阶段

## 2. 先记住最核心的 5 句

1. Spring Boot 启动过程中会发布一系列应用事件。
2. 有些事件发生在 `ApplicationContext` 创建前，所以不能只靠普通 Bean 监听。
3. 启动事件顺序本身就能帮助你理解启动流程。
4. `ApplicationStartedEvent` 不等于应用已经 ready。
5. `ApplicationReadyEvent` 出现在 Runner 调用之后，更接近“准备接流量”。

## 3. 为什么这题值得补

很多人讲启动流程时只会说：

- `SpringApplication.run`
- 创建容器
- refresh
- ready

但如果面试官继续追问：

> 启动过程中有哪些关键事件？

这时如果你完全空掉，就会显得“主线知道一点，但细一点的阶段感没有”。

## 4. 官方文档给出的事件顺序

根据 Spring Boot 官方 `SpringApplication` 参考文档，应用运行时的事件顺序里，常见的有：

1. `ApplicationStartingEvent`
2. `ApplicationEnvironmentPreparedEvent`
3. `ApplicationContextInitializedEvent`
4. `ApplicationPreparedEvent`
5. `ApplicationStartedEvent`
6. `AvailabilityChangeEvent` with `LivenessState.CORRECT`
7. `ApplicationReadyEvent`
8. `AvailabilityChangeEvent` with `ReadinessState.ACCEPTING_TRAFFIC`
9. `ApplicationFailedEvent`（启动异常时）

官方还提到，在 `ApplicationPreparedEvent` 之后、`ApplicationStartedEvent` 之前，还会有：

- `WebServerInitializedEvent`
- `ContextRefreshedEvent`

## 5. 怎么理解前几个事件

### `ApplicationStartingEvent`

> 启动刚开始，还没真正做多少处理。

### `ApplicationEnvironmentPreparedEvent`

> 环境已经准备出来了，但容器还没创建。

### `ApplicationContextInitializedEvent`

> 容器对象已经准备，但 Bean 定义还没正式全部加载。

### `ApplicationPreparedEvent`

> Bean 定义已经加载好了，马上开始 `refresh`。

## 6. 怎么理解 Started 和 Ready

这是非常值得讲清的一点。

### `ApplicationStartedEvent`

> 容器已经 refresh 完了，但 `ApplicationRunner` / `CommandLineRunner` 还没执行。

### `ApplicationReadyEvent`

> Runner 都执行完了，应用真正进入 ready 状态，更接近可以正式对外服务。

一句话记忆：

> Started 不等于 Ready。

## 7. 为什么 Runner 会影响 Ready

官方文档提到：

- `ApplicationRunner`
- `CommandLineRunner`

会在 `SpringApplication.run(...)` 完成前调用。

所以你可以这样答：

> Spring Boot 官方文档里明确说，应用被认为 ready，是在 application 和 command-line runners 被调用之后。这也是为什么 `ApplicationReadyEvent` 比 `ApplicationStartedEvent` 更晚。

## 8. 这题在面试里怎么答最稳

如果面试官问：

> Spring Boot 启动事件你了解吗？

可以这样答：

> 我不会把所有事件名硬背得特别细，但我知道启动过程中有一条比较清晰的阶段事件链。比如启动开始、环境准备完成、容器初始化完成、Bean 定义准备完成、容器 refresh 完成、应用 started、应用 ready，以及启动失败事件。这里最关键的是区分 Started 和 Ready，因为 Ready 出现在 Runner 执行之后，更接近应用真正可以开始接流量的状态。

## 9. 监听事件时要注意什么

官方文档里还提到：

> 有些事件是在 `ApplicationContext` 创建前发出的，所以不能简单地只靠普通 `@Bean` 监听。

你在面试里可以简化成：

> 如果要监听很早期的启动事件，要注意有些事件发生在容器创建前，普通 Bean 监听方式不一定能覆盖到。

## 10. 一句话收尾

> 启动事件题真正的价值，不是背很多事件名，而是帮你把 Spring Boot 启动流程的阶段感讲出来。
