# Spring Boot 高频问答

## 1. 这份文档怎么用

这一篇把 Spring Boot 最常见的面试题单独拎出来，重点处理三类问题：

- 基础定位题
- 自动装配题
- 启动与整合题

## 2. 什么是 Spring Boot

### 问题

什么是 Spring Boot？

### 回答骨架

> Spring Boot 是基于 Spring 生态的一套快速开发框架，核心目标是减少繁琐配置，提升项目搭建、整合和启动效率。

### 追问点

- 为什么它不是替代 Spring
- 它和 Spring、Spring MVC 什么关系

## 3. 为什么有了 Spring 还要 Spring Boot

### 问题

为什么有了 Spring 还要 Spring Boot？

### 回答骨架

> 因为传统 Spring 项目功能很强，但配置和整合相对繁琐。Spring Boot 通过默认约定和工程化整合，把很多手动配置工作收掉了，让项目更快启动、更容易落地。

### 追问点

- Spring Boot 最核心解决了什么问题
- 什么叫约定优于配置

## 4. Spring、Spring MVC、Spring Boot 三者关系

### 问题

Spring、Spring MVC、Spring Boot 是什么关系？

### 回答骨架

> Spring 是基础框架核心，负责 IOC、AOP、事务这些能力；Spring MVC 是 Spring 在 Web 层的解决方案；Spring Boot 则是在 Spring 生态基础上做快速整合和启动。

### 追问点

- Spring Boot 是不是另一个框架
- 为什么很多项目都直接说自己是 Spring Boot 项目

## 5. 什么是自动装配

### 问题

什么是自动装配？

### 回答骨架

> 自动装配就是 Spring Boot 根据当前项目的依赖、配置和运行条件，自动决定加载哪些配置类和 Bean，从而减少手动配置工作。

### 追问点

- 自动装配为什么能减少配置
- 自动装配是不是启动时全配一遍

## 6. 自动装配的核心思想是什么

### 问题

自动装配的核心思想是什么？

### 回答骨架

> 自动装配的核心不是“无脑全配”，而是“按条件装配”。只有满足某些条件，对应的自动配置才会真正生效。

### 追问点

- 什么叫条件装配
- 条件注解的作用是什么

## 7. `@SpringBootApplication` 是什么

### 问题

`@SpringBootApplication` 是什么？

### 回答骨架

> `@SpringBootApplication` 是 Spring Boot 启动类上的核心组合注解，可以理解成 Spring Boot 启动的统一入口。

### 追问点

- 里面大概包含哪些能力
- `@EnableAutoConfiguration` 是干什么的

## 8. `@EnableAutoConfiguration` 是什么

### 问题

`@EnableAutoConfiguration` 是干什么的？

### 回答骨架

> `@EnableAutoConfiguration` 的作用是开启 Spring Boot 的自动装配能力，让 Spring Boot 根据条件去加载合适的自动配置类。

### 追问点

- 什么是自动配置类
- 它和条件注解有什么关系

## 9. `starter` 是什么

### 问题

`starter` 是什么？

### 回答骨架

> `starter` 是 Spring Boot 提供的一组场景化依赖集合，它把某类功能常用的依赖和整合方式先准备好，开发者引入对应 starter 后，就能更快搭好这类能力。

### 追问点

- `starter` 和自动装配是什么关系
- 为什么说它解决的是依赖整合问题

## 10. 常见条件注解怎么讲

### 问题

Spring Boot 常见条件注解知道哪些？

### 回答骨架

> 常见的像 `@ConditionalOnClass`、`@ConditionalOnMissingBean`、`@ConditionalOnProperty`，它们本质上都是在判断某套自动配置该不该生效。

### 追问点

- 为什么需要这些条件注解
- 没有条件装配会怎样

## 11. 最值得优先背的 8 题

1. 什么是 Spring Boot
2. 为什么有了 Spring 还要 Spring Boot
3. Spring、Spring MVC、Spring Boot 的关系
4. 什么是自动装配
5. 自动装配的核心思想是什么
6. `@SpringBootApplication` 是什么
7. `@EnableAutoConfiguration` 是干什么的
8. `starter` 是什么

## 12. 一句话收尾

> Spring Boot 高频题最关键的，不是把原理讲得多深，而是先把“它为什么出现、怎么减少配置、自动装配为什么不会失控”讲清楚。
