# 013-JVM

## 1. 这一章怎么学

JVM 这一章不适合一上来就扎进特别碎的参数、回收器细节或者调优命令。

更合适的顺序是：

1. 先知道 JVM 是什么，为什么 Java 会强调 JVM。
2. 再理解 JVM 内存结构大概有哪些。
3. 再进入堆、栈、方法区这几个高频点。
4. 然后补 GC 和常见垃圾回收器。
5. 再补类加载、双亲委派、JMM、`volatile`。
6. 最后再看 OOM、Full GC、线上排查和调优。

这一章复习时，建议始终围绕下面这几条主线：

- 运行：Java 程序为什么能跑起来，JVM 做了什么。
- 内存：对象放哪，方法怎么执行，哪些区域最常被问。
- 回收：对象什么时候该回收，GC 大概怎么做。
- 加载：类怎么从 `.class` 变成 JVM 里的可用数据。
- 并发：JMM、可见性、有序性、`volatile` 怎么理解。
- 排障：OOM、Full GC、CPU 飙高、调优一般怎么说。

## 2. 当前目录说明

当前 `013-JVM` 下面已经有一套从别处 copy 过来的 JVM 资料，放在：

- `006-JVM`
- `mock-and-oral`
- `interview-experience`
- `pro-jvm`

这套资料可以作为现成内容库继续复用。

但当前这套笔记的目标不是简单搬运，而是继续整理成统一版复习结构。所以顶层会逐步补齐：

- 入口文档
- 主线专题
- 高频问题
- 回答版
- checklist
- 模拟追问

## 3. 当前建议先看什么

当前阶段最适合先看：

1. `jvm-basic-overview.md`
2. `006-JVM/01-JVM基础总览-内存结构-GC-类加载.md`
3. `006-JVM/02-JVM垃圾回收与常见回收器.md`
4. `006-JVM/03-JVM类加载与双亲委派.md`
5. `006-JVM/06-JVM调优与线上排查.md`

## 4. 后续会逐步补哪些正式文档

后续建议逐步整理出这些正式文档：

- `jvm-basic-overview.md`
- `jvm-memory-structure-note.md`
- `jvm-gc-note.md`
- `jvm-classloading-note.md`
- `jvm-jmm-volatile-note.md`
- `jvm-oom-troubleshooting-note.md`
- `jvm-interview-high-frequency.md`
- `jvm-interview-answers.md`
- `jvm-review-checklist.md`
- `jvm-object-creation-reference-note.md`
- `jvm-mock-chain-questions.md`
- `jvm-final-review.md`
- `jvm-oral-answers.md`
- `jvm-from-basic-to-pro-roadmap.md`
- `mock-and-oral/jvm-1min-3min-5min-answer-pack.md`
- `mock-and-oral/jvm-mock-qa-script.md`
- `mock-and-oral/README.md`
- `mock-and-oral/jvm-handwritten-qa.md`
- `mock-and-oral/jvm-last-day-revision.md`
- `mock-and-oral/jvm-self-check-scorecard.md`
- `mock-and-oral/jvm-project-scene-answers.md`
- `mock-and-oral/jvm-final-mock-paper.md`
- `mock-and-oral/jvm-cheatsheet-one-page.md`
- `interview-experience/README.md`
- `interview-experience/jvm-interview-experience-high-frequency.md`
- `interview-experience/jvm-interview-experience-answer-notes.md`
- `pro-jvm/jvm-jit-note.md`
- `pro-jvm/jvm-object-header-lock-note.md`
- `pro-jvm/jvm-safepoint-stw-note.md`
- `pro-jvm/jvm-gc-log-reading.md`
- `pro-jvm/jvm-direct-memory-note.md`
- `pro-jvm/jvm-classloader-metaspace-advanced.md`
- `pro-jvm/jvm-tuning-parameters-note.md`
- `pro-jvm/jvm-advanced-case-study.md`
- `pro-jvm/pro-jvm-mock-questions.md`
- `pro-jvm/jvm-object-allocation-note.md`
- `pro-jvm/jvm-finalize-reference-queue-note.md`
- `pro-jvm/jvm-modern-gc-note.md`
- `pro-jvm/jvm-jdk-version-differences-note.md`
- `pro-jvm/jvm-final-immutable-jmm-note.md`
- `pro-jvm/jvm-live-diagnosis-note.md`

## 5. 先记住的一句话

> JVM 面试的核心不是死背名词，而是围绕内存结构、GC、类加载、JMM 和线上排查这几条主线，解释清楚“程序怎么跑、对象放哪、内存怎么回收、出了问题怎么查”。 
