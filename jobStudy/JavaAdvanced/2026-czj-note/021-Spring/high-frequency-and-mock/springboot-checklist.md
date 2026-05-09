# Spring Boot 考前 Checklist

## 1. 这份文档怎么用

这一篇是 Spring Boot 考前自检表。

如果你不想把 Spring Boot 那几篇重新全翻一遍，就对着这份 checklist 快速过：

- 会不会定义
- 会不会一句话解释
- 会不会接追问
- 能不能结合项目说

## 2. 基础定位

- 我能不能一句话说清什么是 Spring Boot。
- 我能不能解释为什么 Spring Boot 不是替代 Spring。
- 我能不能说清 Spring、Spring MVC、Spring Boot 三者关系。
- 我能不能讲出 Spring Boot 最核心解决了什么问题。

## 3. 为什么需要 Spring Boot

- 我能不能解释为什么有了 Spring 还要 Spring Boot。
- 我能不能说清“传统 Spring 配置偏重”具体重在哪里。
- 我能不能说出 Spring Boot 带来的工程化收益。
- 我能不能解释什么叫约定优于配置。

## 4. 自动装配

- 我能不能一句话说清什么是自动装配。
- 我能不能强调自动装配的核心是“按条件装配”。
- 我知不知道自动装配不是“启动时全都配一遍”。
- 我能不能说出自动装配为什么能减少配置。

## 5. 启动入口

- 我能不能解释 `@SpringBootApplication` 是什么。
- 我能不能说出它是启动类上的核心组合注解。
- 我能不能讲出它大概包含配置类声明、自动装配、组件扫描三层能力。
- 我能不能解释 `@EnableAutoConfiguration` 的作用。

## 6. 条件装配

- 我能不能解释什么叫条件装配。
- 我能不能说出条件通常会看类、Bean、配置属性这些信息。
- 我能不能讲出常见条件注解的共同作用。
- 我能不能说出 `@ConditionalOnClass`、`@ConditionalOnMissingBean`、`@ConditionalOnProperty`。

## 7. starter

- 我能不能解释什么是 `starter`。
- 我能不能说出 `starter` 为什么有价值。
- 我能不能讲清 `starter` 和自动装配的关系。
- 我能不能用一句话区分“依赖整合”和“配置生效”。

## 8. 项目表达

- 我能不能结合项目说 Spring Boot 的价值。
- 我能不能说出项目里最常见的 Spring Boot 能力。
- 我能不能解释如果没有 Spring Boot，项目开发哪里会更麻烦。
- 我能不能把 Spring Boot 说成“工程化整合方案”，而不是只会说“少写配置”。

## 9. 开口表达

- 我现在回答 Spring Boot 时，是不是还像在背定义。
- 我能不能在 30 秒内讲清“什么是 Spring Boot”。
- 我能不能在 1 分钟内讲清“自动装配”。
- 我能不能在 2 分钟内把 Spring Boot 整条线串起来。

## 10. 如果时间只够最后过一遍

优先检查这 8 个：

1. 什么是 Spring Boot
2. 为什么有了 Spring 还要 Spring Boot
3. Spring、Spring MVC、Spring Boot 的关系
4. 什么是自动装配
5. 为什么自动装配不是“全都自动配”
6. `@SpringBootApplication` 是什么
7. `@EnableAutoConfiguration` 是干什么的
8. `starter` 是什么

## 11. 一句话收尾

> Spring Boot checklist 的意义，不是让你全背下来，而是快速定位“你到底是卡在基础定位，还是卡在自动装配这条线”。
