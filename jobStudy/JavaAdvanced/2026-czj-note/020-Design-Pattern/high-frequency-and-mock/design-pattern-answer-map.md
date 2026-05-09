# 设计模式问题 - 文档 - 答法映射表

## 1. 这份文档怎么用

这一篇不是新增知识点，而是把这一章已经写过的材料串成导航图。

它主要解决三个问题：

- 某个面试问题来了，我应该先看哪篇
- 某类问题该怎么组织回答
- 考前时间不多时，我该优先看哪些文档

## 2. 如果面试官问“什么是设计模式”

### 先看文档

- `design-pattern-high-frequency-qa.md`
- `design-pattern-oral-answer-pack.md`
- `design-pattern-1min-3min-answer-pack.md`

### 推荐答法路线

1. 先说设计模式不是固定模板代码
2. 再说它解决的是重复出现的设计问题
3. 最后补一句价值是降耦合、提扩展、拆职责

## 3. 如果面试官问“为什么要学设计模式”

### 先看文档

- `design-pattern-high-frequency-qa.md`
- `design-pattern-oral-answer-pack.md`
- `design-pattern-final-checklist.md`

### 推荐答法路线

1. 先说不是为了背八股
2. 再说真实价值是面对复杂业务时更容易维护和扩展
3. 最后举“规则变多、流程变长、对象创建复杂”这类问题

## 4. 如果面试官问“你最熟哪些设计模式”

### 先看文档

- `design-pattern-one-page-cheatsheet.md`
- `design-pattern-1min-3min-answer-pack.md`
- `design-pattern-final-checklist.md`

### 推荐答法路线

1. 优先讲高频的几个，不要把 23 种全背出来
2. 推荐顺序：单例、工厂、代理、策略、模板方法、责任链、观察者
3. 每个模式至少带一句场景

## 5. 如果面试官问“单例怎么写”

### 先看文档

- `singleton-note.md`
- `design-pattern-high-frequency-qa.md`
- `design-pattern-1min-3min-answer-pack.md`

### 推荐答法路线

1. 先说目标是全局唯一实例
2. 再说线程安全写法
3. 面试官继续追问时接懒汉、饿汉、双重检查锁、静态内部类、枚举单例

## 6. 如果面试官问“工厂模式解决什么问题”

### 先看文档

- `factory-pattern-note.md`
- `comparison/factory-vs-direct-new.md`
- `design-pattern-1min-3min-answer-pack.md`

### 推荐答法路线

1. 先说它不是为了少写一个 `new`
2. 再说它的价值是封装创建逻辑、降低耦合
3. 最后补一句什么时候直接 `new` 也没问题

## 7. 如果面试官问“代理模式和 AOP 的关系”

### 先看文档

- `proxy-pattern-note.md`
- `design-pattern-spring-mapping-note.md`
- `design-pattern-1min-3min-answer-pack.md`

### 推荐答法路线

1. 先说 AOP 不改原业务代码
2. 再说通过代理织入事务、日志、权限
3. 如果继续追问，再接 JDK 动态代理和 CGLIB

## 8. 如果面试官问“策略模式适合什么场景”

### 先看文档

- `strategy-pattern-note.md`
- `design-pattern-project-answer-pack.md`
- `design-pattern-1min-3min-answer-pack.md`

### 推荐答法路线

1. 先说适合一组可替换规则
2. 再说为什么适合替代长 `if else`
3. 最后给业务例子，比如优惠、支付、审核规则

## 9. 如果面试官问“策略和模板方法有什么区别”

### 先看文档

- `comparison/strategy-vs-template-method.md`
- `design-pattern-compare-note.md`
- `design-pattern-trap-questions.md`

### 推荐答法路线

1. 先说策略偏规则替换
2. 再说模板方法偏流程固定、步骤变化
3. 最后用一个业务场景把区别落地

## 10. 如果面试官问“代理和装饰器有什么区别”

### 先看文档

- `comparison/proxy-vs-decorator.md`
- `design-pattern-compare-note.md`
- `design-pattern-trap-questions.md`

### 推荐答法路线

1. 先说两者结构像，但目标不同
2. 代理偏控制访问和统一增强
3. 装饰器偏动态叠加能力

## 11. 如果面试官问“观察者和发布订阅有什么区别”

### 先看文档

- `comparison/observer-vs-pubsub.md`
- `design-pattern-compare-note.md`
- `observer-pattern-note.md`

### 推荐答法路线

1. 先说两者都有一对多通知味道
2. 再说观察者偏对象通知，发布订阅偏中间通道解耦
3. 最后接监听器和 MQ 的区别

## 12. 如果面试官问“Spring 中用到了哪些设计模式”

### 先看文档

- `design-pattern-spring-mapping-note.md`
- `design-pattern-real-interview-mixed-questions.md`
- `design-pattern-1min-3min-answer-pack.md`

### 推荐答法路线

1. 工厂：Bean 创建和容器管理
2. 单例思想：默认单例 Bean
3. 代理：AOP、事务、权限增强
4. 模板方法：`Template` 系列
5. 适配器：`HandlerAdapter`
6. 观察者、责任链、策略作为补充

## 13. 如果面试官问“你项目里用过设计模式吗”

### 先看文档

- `design-pattern-project-scene-questions.md`
- `design-pattern-project-answer-pack.md`
- `design-pattern-mock-oral-script.md`

### 推荐答法路线

1. 不要先背模式名
2. 先讲问题：规则太多、流程太长、创建太耦合、公共逻辑散落
3. 再讲怎么拆
4. 最后补一句更接近哪种模式思想

## 14. 如果面试官连续追问，你该看哪篇

### 优先文档

- `design-pattern-mock-chain-questions.md`
- `design-pattern-mock-oral-script.md`
- `design-pattern-final-mock-paper.md`

### 作用

- `mock-chain-questions`：看一层层追问思路
- `mock-oral-script`：练连续口语节奏
- `final-mock-paper`：整体模拟抽题

## 15. 如果你只有 10 分钟复习时间

### 推荐顺序

1. `design-pattern-one-page-cheatsheet.md`
2. `design-pattern-1min-3min-answer-pack.md`
3. `design-pattern-final-checklist.md`

## 16. 如果你只有 30 分钟复习时间

### 推荐顺序

1. `design-pattern-one-page-cheatsheet.md`
2. `design-pattern-1min-3min-answer-pack.md`
3. `design-pattern-compare-note.md`
4. `design-pattern-spring-mapping-note.md`
5. `design-pattern-project-answer-pack.md`
6. `design-pattern-final-checklist.md`

## 17. 如果你想做一轮完整模拟

### 推荐顺序

1. `design-pattern-mock-oral-script.md`
2. `design-pattern-mock-chain-questions.md`
3. `design-pattern-final-mock-paper.md`

## 18. 一句话收尾

> 这一章真正高效的复习方式，不是从头到尾硬看一遍，而是先明确“我在答哪类问题”，再回到对应文档精准补齐。
