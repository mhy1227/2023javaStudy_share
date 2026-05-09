# 020-Design-Pattern

## 1. 这一章是干什么的

这一章专门整理 Java 面试里最常见的设计模式。

它不是要把所有模式都背成百科，而是重点整理：

- 设计模式到底解决什么问题
- 常见模式的核心思想
- 面试里怎么讲得简洁、像项目表达
- 这些模式和 Spring、业务代码、框架源码怎么串起来

## 2. 为什么值得单独开目录

因为设计模式在面试里有两种问法：

- 直接问：你知道哪些设计模式、单例怎么写、工厂和策略区别是什么
- 间接问：Spring 里用了哪些设计模式、你项目里有没有用过策略/模板/责任链

所以这章最重要的不是“背名字”，而是要能把模式和实际代码场景对应起来。

## 3. 当前目录结构

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
- `comparison/`
- `high-frequency-and-mock/`

## 4. 怎么看最顺

建议顺序：

1. `design-pattern-basic-overview.md`
2. `singleton-note.md`
3. `factory-pattern-note.md`
4. `proxy-pattern-note.md`
5. `strategy-pattern-note.md`
6. `observer-pattern-note.md`
7. `chain-of-responsibility-note.md`
8. `template-method-note.md`
9. `adapter-pattern-note.md`
10. `decorator-pattern-note.md`
11. `comparison/strategy-vs-template-method.md`
12. `comparison/proxy-vs-decorator.md`
13. `comparison/observer-vs-pubsub.md`
14. `comparison/factory-vs-direct-new.md`
15. `high-frequency-and-mock/design-pattern-high-frequency-qa.md`
16. `high-frequency-and-mock/design-pattern-project-scene-questions.md`
17. `high-frequency-and-mock/design-pattern-mock-chain-questions.md`
18. `high-frequency-and-mock/design-pattern-oral-answer-pack.md`
19. `high-frequency-and-mock/design-pattern-checklist.md`
20. `high-frequency-and-mock/design-pattern-trap-questions.md`
21. `high-frequency-and-mock/design-pattern-final-mock-paper.md`
22. `high-frequency-and-mock/design-pattern-compare-note.md`
23. `high-frequency-and-mock/design-pattern-spring-mapping-note.md`
24. `high-frequency-and-mock/design-pattern-real-interview-mixed-questions.md`
25. `high-frequency-and-mock/design-pattern-project-answer-pack.md`
26. `high-frequency-and-mock/design-pattern-1min-3min-answer-pack.md`
27. `high-frequency-and-mock/design-pattern-final-checklist.md`
28. `high-frequency-and-mock/design-pattern-mock-oral-script.md`
29. `high-frequency-and-mock/design-pattern-answer-map.md`
30. `high-frequency-and-mock/design-pattern-topic-roadmap.md`
31. `high-frequency-and-mock/design-pattern-last-10-minutes.md`
32. `high-frequency-and-mock/design-pattern-one-page-cheatsheet.md`

## 5. 一句话记住

> 设计模式不是背模板代码，而是学会“面对某类重复问题时，用什么更稳定的设计思路去解决”。
