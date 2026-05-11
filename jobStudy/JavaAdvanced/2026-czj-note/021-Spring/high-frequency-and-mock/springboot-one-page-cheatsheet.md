# Spring Boot 一页速背版

## 1. Spring Boot 一句话

Spring Boot 是基于 Spring 生态的一套快速开发和工程化整合方案，核心目标是减少繁琐配置，提升项目搭建、整合和启动效率。

## 2. 和 Spring / Spring MVC 的关系

- Spring：基础能力底座，解决 IOC、AOP、事务
- Spring MVC：Web 层请求处理
- Spring Boot：快速整合、快速启动、工程化配置

一句话记忆：

> Spring 是底座，Spring MVC 是 Web 层，Spring Boot 是整合和启动层。

## 3. 为什么需要 Spring Boot

- 传统 Spring 功能强，但配置偏重
- 中间件整合成本高
- 项目搭建和启动流程繁琐
- Spring Boot 通过默认约定把样板工作收掉

## 4. 约定优于配置

- 常见场景先给默认方案
- 特殊情况再覆盖
- 不要求每次都从零手写所有配置

## 5. 自动装配

- 定义：根据依赖、配置和运行条件，自动决定加载哪些配置类和 Bean
- 核心：按条件装配，不是无脑全配
- 价值：减少手动配置，提升整合效率

一句话记忆：

> 自动装配不是“都装”，而是“满足条件才装”。

## 6. 启动入口

- `@SpringBootApplication`：启动类上的核心组合注解
- 可以先记三层能力：
- 配置类声明
- 开启自动装配
- 组件扫描

常记名字：

- `@SpringBootConfiguration`
- `@EnableAutoConfiguration`
- `@ComponentScan`

## 7. `@EnableAutoConfiguration`

- 作用：开启自动装配能力
- 本质：让 Spring Boot 根据条件去加载合适的自动配置类

## 8. 条件装配

- 会看什么：
- 类路径里有没有某个类
- 容器里有没有某个 Bean
- 配置文件里有没有某个属性

常见条件注解：

- `@ConditionalOnClass`
- `@ConditionalOnMissingBean`
- `@ConditionalOnProperty`

## 9. starter

- `starter`：场景化依赖集合
- 作用：把某类功能常用依赖先准备好
- 价值：统一依赖组合方式，降低整合成本

## 10. starter 和自动装配的关系

- `starter`：负责带依赖
- 自动装配：负责让对应配置按条件生效

一句话记忆：

> `starter` 带材料，自动装配拼材料。

## 11. 高频题速背

1. 什么是 Spring Boot
2. 为什么有了 Spring 还要 Spring Boot
3. Spring、Spring MVC、Spring Boot 的关系
4. 什么是自动装配
5. 为什么自动装配不是“全都自动配”
6. `@SpringBootApplication` 是什么
7. `@EnableAutoConfiguration` 是干什么的
8. `starter` 是什么

## 12. 项目化表达一句话

如果结合项目讲：

> Spring Boot 的价值不只是少写配置，而是把项目启动、配置管理和常见中间件整合这件事工程化了。
