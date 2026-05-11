# 设计模式复习路线图

## 1. 这份文档怎么用

这一篇不是新知识点，而是把这一章已经整理好的内容串成一条完整复习路线。

它适合三种场景：

- 你第一次系统复习设计模式，不知道从哪开始
- 你已经看过很多文档，但感觉内容有点散
- 你考前时间有限，需要按阶段抓重点

## 2. 整体复习主线

设计模式这一章，建议按下面这条线走：

1. 先建立基础概念
2. 再抓高频模式
3. 再练高频对比题
4. 再和 Spring 场景串起来
5. 再补项目表达
6. 最后做速答、checklist、模拟题

## 3. 第一阶段：先把主线建起来

### 目标

- 知道设计模式到底在解决什么问题
- 知道哪些模式是 Java 面试最高频
- 不追求一上来全背 23 种

### 推荐文档

- `design-pattern-basic-overview.md`
- `singleton-note.md`
- `factory-pattern-note.md`
- `proxy-pattern-note.md`
- `strategy-pattern-note.md`
- `observer-pattern-note.md`
- `chain-of-responsibility-note.md`
- `template-method-note.md`
- `adapter-pattern-note.md`
- `decorator-pattern-note.md`

### 阶段完成标准

- 你能说清每个模式解决什么问题
- 你能给出至少一个典型场景
- 你不会把所有模式讲成“就是为了减少 if else”

## 4. 第二阶段：先把高频题讲顺

### 目标

- 把最常见面试问题讲顺
- 把书面定义改成能说出口的表达

### 推荐文档

- `high-frequency-and-mock/design-pattern-high-frequency-qa.md`
- `high-frequency-and-mock/design-pattern-oral-answer-pack.md`
- `high-frequency-and-mock/design-pattern-1min-3min-answer-pack.md`
- `high-frequency-and-mock/design-pattern-one-page-cheatsheet.md`

### 阶段完成标准

- 你能 30 秒讲清一个模式的核心价值
- 你能 1 分钟说清“问题 + 模式 + 场景”
- 你能 3 分钟接住一轮正常追问

## 5. 第三阶段：把最容易混的题拉直

### 目标

- 解决“长得像但目标不同”的混淆
- 提前处理陷阱题

### 推荐文档

- `high-frequency-and-mock/design-pattern-compare-note.md`
- `comparison/strategy-vs-template-method.md`
- `comparison/proxy-vs-decorator.md`
- `comparison/observer-vs-pubsub.md`
- `comparison/factory-vs-direct-new.md`
- `high-frequency-and-mock/design-pattern-trap-questions.md`

### 阶段完成标准

- 你能区分策略和模板方法
- 你能区分代理和装饰器
- 你能区分观察者和发布订阅
- 你能解释工厂为什么不只是“少写一个 new”

## 6. 第四阶段：和 Spring 体系串起来

### 目标

- 让设计模式不再只是抽象概念
- 能回答“Spring 中用了哪些设计模式”

### 推荐文档

- `high-frequency-and-mock/design-pattern-spring-mapping-note.md`
- `high-frequency-and-mock/design-pattern-real-interview-mixed-questions.md`
- `high-frequency-and-mock/design-pattern-answer-map.md`

### 阶段完成标准

- 你能讲工厂和 Bean 创建的关系
- 你能讲代理和 AOP 的关系
- 你能讲 `Template` 系列和模板方法的关系
- 你能讲 `HandlerAdapter` 和适配器的关系

## 7. 第五阶段：把项目表达练真实

### 目标

- 避免一开口就在背模式名
- 学会先讲问题，再讲设计，再落到模式

### 推荐文档

- `high-frequency-and-mock/design-pattern-project-scene-questions.md`
- `high-frequency-and-mock/design-pattern-project-answer-pack.md`
- `high-frequency-and-mock/design-pattern-real-interview-mixed-questions.md`

### 阶段完成标准

- 你能回答“项目里用过设计模式吗”
- 你不会机械说“这里就是某某模式”
- 你能把策略、责任链、工厂、代理落到业务问题上

## 8. 第六阶段：考前收口

### 目标

- 用最短时间把整章拉通
- 进入面试口语状态

### 推荐文档

- `high-frequency-and-mock/design-pattern-final-checklist.md`
- `high-frequency-and-mock/design-pattern-mock-oral-script.md`
- `high-frequency-and-mock/design-pattern-final-mock-paper.md`
- `high-frequency-and-mock/design-pattern-answer-map.md`

### 阶段完成标准

- 你知道自己最薄弱的是哪一类题
- 你能连续回答一轮设计模式追问
- 你能在 10 分钟内快速回看这一章

## 9. 如果你只有 1 天时间

### 建议顺序

1. `design-pattern-one-page-cheatsheet.md`
2. `design-pattern-1min-3min-answer-pack.md`
3. `design-pattern-compare-note.md`
4. `design-pattern-spring-mapping-note.md`
5. `design-pattern-project-answer-pack.md`
6. `design-pattern-final-checklist.md`

## 10. 如果你有 3 天时间

### 第一天

- 过顶层主线和高频模式

### 第二天

- 过对比题、Spring 映射、项目表达

### 第三天

- 过速答、checklist、模拟口语和模拟卷

## 11. 如果你有 7 天时间

### 建议节奏

1. 第 1 到 2 天：顶层模式主线
2. 第 3 天：高频问答与口语版
3. 第 4 天：高频对比和陷阱题
4. 第 5 天：Spring 映射和公开面经题
5. 第 6 天：项目答法与 mock 追问
6. 第 7 天：最终 checklist 和模拟卷

## 12. 最后怎么判断这一章是不是复习到位了

你只要能稳定回答下面 5 类问题，这一章基本就算过关：

- 设计模式是什么、为什么学
- 几个高频模式的核心价值和场景
- 高频对比题
- Spring 里的模式落地
- 项目里怎么把模式讲得真实

## 13. 一句话收尾

> 设计模式这章最稳的复习方式，不是横着背一堆名字，而是按“基础 -> 高频 -> 对比 -> Spring -> 项目 -> 模拟”这条线一层层往下压。
