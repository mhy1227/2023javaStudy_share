# Spring Boot Runner / Listener 笔记

## 1. 这份文档怎么用

这一篇专门把 Spring Boot 里比较容易混的三件事拉直：

- `ApplicationRunner`
- `CommandLineRunner`
- 启动事件 / Listener

它和 `springboot-startup-flow-note.md`、`springboot-startup-events-note.md` 的关系是：

- 启动流程讲主干
- 启动事件讲阶段
- 这一篇讲“启动最后执行的钩子”和“事件监听”怎么区分

## 2. 先记住最核心的 6 句

1. `ApplicationRunner` 和 `CommandLineRunner` 都是应用启动后执行自定义逻辑的钩子。
2. 两者都发生在 `SpringApplication.run(...)` 完成前的最后阶段。
3. `ApplicationRunner` 和 `CommandLineRunner` 的主要区别在参数封装方式。
4. Listener 更偏事件监听，不等同于 Runner。
5. 启动事件是阶段通知，Runner 是启动后执行逻辑的入口。
6. 面试里最值钱的是把 “流程 -> 事件 -> Runner” 这条线讲顺。

## 3. `ApplicationRunner` 是什么

可以这样答：

> `ApplicationRunner` 是 Spring Boot 提供的一个启动后回调接口，适合在应用完成启动前的最后阶段执行一些初始化逻辑。

## 4. `CommandLineRunner` 是什么

可以这样答：

> `CommandLineRunner` 和 `ApplicationRunner` 作用很像，也是应用启动后执行逻辑的入口，只是它直接接收原始命令行参数。

## 5. 两者区别怎么讲最稳

可以这样答：

> 两者的核心差别不在时机，而在参数封装。`CommandLineRunner` 接收原始字符串数组参数，`ApplicationRunner` 接收封装后的 `ApplicationArguments`，所以如果要更方便地处理参数，一般会更偏 `ApplicationRunner`。

一句话版：

> 一个拿原始参数，一个拿封装参数。

## 6. 它们在启动流程里的位置

官方文档提到，Runner 会在应用被认为 ready 之前执行。

面试里你可以这样答：

> 从启动流程上看，Runner 发生在容器 refresh 完成之后、应用真正 ready 之前，所以它适合做一些启动后初始化逻辑，但不适合塞太重的阻塞任务。

## 7. Listener / 事件监听怎么理解

可以这样答：

> Listener 更偏事件驱动，也就是在 Spring Boot 启动过程中监听某个阶段事件，然后做对应处理。它和 Runner 不一样，Runner 更像“启动末尾给你一个执行入口”，而 Listener 是“在某个阶段触发时收到通知”。

## 8. Runner 和 Listener 最容易混在哪里

很多人会混成：

- 都是启动后做点事情

这说法不够稳。

更好的区分是：

- Runner：更像统一的启动后执行入口
- Listener：更像阶段事件监听器

## 9. 如果面试官问“项目里一般怎么用”

你可以这样答：

> 如果项目里确实需要在启动后做一些初始化动作，比如缓存预热、字典加载、某些轻量级准备逻辑，可以考虑 Runner；如果更关注启动过程中的某个阶段，比如环境准备完成、应用 ready、启动失败这些状态变化，那更适合从事件监听的角度看。

## 10. 一版适合面试的完整回答

> Spring Boot 里 `ApplicationRunner` 和 `CommandLineRunner` 都是应用启动后执行自定义逻辑的钩子，它们都发生在 `SpringApplication.run(...)` 完成前的最后阶段。两者最核心的区别在参数封装，前者接收 `ApplicationArguments`，后者接收原始命令行参数。Listener 则不一样，它更偏事件监听，关注的是启动过程中的某个阶段事件，比如环境准备完成、应用 started、应用 ready 或启动失败等。所以如果要一句话区分，我会说 Runner 是启动后执行入口，Listener 是阶段事件监听入口。 

## 11. 最容易答错的点

- 把 Runner 和 Listener 说成一回事
- 不知道 `ApplicationRunner` 和 `CommandLineRunner` 的区别
- 以为 `ApplicationStartedEvent` 之后应用就一定 ready
- 不知道 Runner 会影响 ready 时机

## 12. 一句话收尾

> Runner / Listener 这题真正要讲清的，不是接口名，而是启动流程里“谁负责阶段通知，谁负责最后执行逻辑”。
