# Spring Boot 3 迁移问答

## 1. 这份文档怎么用

这一篇把 Spring Boot 3 迁移相关的高频问法整理成更适合面试的问答形式。

它和 `springboot-version-diff-note.md` 的区别是：

- 那一篇更偏知识整理
- 这一篇更偏“怎么问、怎么答”

## 2. 最常见的起手题

### 问题

你了解 Spring Boot 2 升 3 的主要变化吗？

### 回答骨架

> 如果按面试里最常见的主线，我会重点看 2.x 到 3.x 的变化。最直接的是 Java 基线提升到 17，底层切到 Spring Framework 6，然后是 Jakarta 命名空间从 `javax.*` 切到 `jakarta.*`，再往后还有 Spring Security 6、配置属性迁移，以及自动配置口径上的更新。

## 3. Java 版本为什么一定会被问

### 问题

升级到 Boot 3，最先要看什么？

### 回答骨架

> 最先要看 Java 基线是不是满足。官方迁移指南明确提到 Boot 3 需要 Java 17 或更高版本，所以如果项目还停在低版本 JDK，这一步就先卡住了。

## 4. Jakarta 命名空间怎么答

### 问题

Boot 3 迁移时最典型的代码层变化是什么？

### 回答骨架

> 最典型的就是 Jakarta 命名空间迁移。很多原来 `javax.*` 的依赖和 import，在升级到 Boot 3 后都要切到 `jakarta.*`。

## 5. Spring Framework 6 为什么也要提

### 问题

为什么不能只说 Boot 3 自己变了？

### 回答骨架

> 因为 Boot 3 是建立在 Spring Framework 6 之上的，所以升级不只是换了 Boot 版本，底层 Spring 基线也一起抬升了。

## 6. 配置属性迁移怎么答

### 问题

升级时除了改依赖，还要看什么？

### 回答骨架

> 还要检查配置属性变化。官方迁移资料提到一些配置项会被改名或移除，并且提供了 `spring-boot-properties-migrator` 这样的迁移辅助模块。

## 7. 安全相关为什么也经常会被提

### 问题

为什么升级 Boot 3 时经常顺带提到 Spring Security？

### 回答骨架

> 因为 Boot 3 使用的是 Spring Security 6，所以安全这条线经常也要一起评估，不能只看 Boot 自己的版本号。

## 8. 自动配置发现机制这题怎么答

### 问题

你还会只说自动配置靠 `spring.factories` 吗？

### 回答骨架

> 如果讲旧版本语境，说自动配置通过 `spring.factories` 被发现没问题；但如果讲较新的 Spring Boot 版本语境，最好补一句自动配置发现机制已经转向 `META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports` 这类方式，别把旧说法讲成唯一答案。

## 9. 如果没真正做过迁移项目，怎么答更稳

### 问题

如果你没做过完整升级项目，版本差异题怎么答？

### 回答骨架

> 我不会硬说自己做过大规模升级，但我知道面试里最关键的差异主要集中在 Java 基线、Jakarta 命名空间、Spring Framework 6、安全依赖以及自动配置口径更新这些地方。

## 10. 一版适合面试的完整回答

> 如果从面试里最常见的主线看，Spring Boot 2.x 升 3.x 最值得关注的是几件事。第一是 Java 基线提升到 17，第二是底层切到 Spring Framework 6，第三是 Jakarta 命名空间从 `javax.*` 迁移到 `jakarta.*`，这对依赖和 import 都会有影响。再往后还有 Spring Security 6、配置属性迁移，以及自动配置发现机制口径的更新。所以这类题我一般不会把它答成很多零散小改动，而是会抓住“运行时基础没变，但工程基线和依赖生态明显变了”这条主线。 

## 11. 一句话收尾

> Spring Boot 3 迁移题最重要的，不是把细节背满，而是把 2.x 到 3.x 的主线变化和迁移风险说清楚。
