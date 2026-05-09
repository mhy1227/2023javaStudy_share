# JVM 从基础到 Pro 的复习路线图

## 1. 这份文档怎么用

这一篇不是某一个知识点笔记，而是整个 `013-JVM` 的复习路线图。

它主要解决：

- 现在这套 JVM 资料到底怎么用
- 基础版和 pro 版之间怎么衔接
- 先学什么，后学什么
- 学到什么程度算“过线”

如果你不想一头扎进文档海里，这篇就是总导航。

## 2. 整个 JVM 现在分成哪几层

你现在这套 `013-JVM`，其实已经可以分成 4 层：

1. 基础主线层
2. 输出训练层
3. 外部面经层
4. Pro 进阶层

这 4 层的作用分别不一样。

## 3. 第一层：基础主线层

这一层对应顶层那些核心文档，主要解决：

- JVM 是什么
- 内存结构
- GC
- 类加载
- JMM / `volatile`
- OOM / 排查

你可以把这一层理解成：

> 这是 JVM 的“骨架”。

如果这层不稳，后面所有进阶内容都会变得很虚。

这一层的关键文件包括：

- `jvm-basic-overview.md`
- `jvm-memory-structure-note.md`
- `jvm-gc-note.md`
- `jvm-classloading-note.md`
- `jvm-jmm-volatile-note.md`
- `jvm-oom-troubleshooting-note.md`

## 4. 第二层：输出训练层

这一层主要在：

- `mock-and-oral`

它不是继续补知识点，而是训练你：

- 1 分钟怎么讲
- 3 分钟怎么讲
- 被追问时怎么接
- 哪些题最容易答错
- 面试前一天看什么

这一层你可以理解成：

> 这是 JVM 的“说出来”层。

如果基础会了，但一开口就乱，这一层就是最关键的。

## 5. 第三层：外部面经层

这一层主要在：

- `interview-experience`

它的作用是：

- 看公开面经里 JVM 到底常问什么
- 验证你前面准备的方向有没有偏
- 理解真实面试里最常出现的追问链

这一层你可以理解成：

> 这是 JVM 的“市场验证层”。

也就是说，你不是自己觉得哪些题重要，而是公开面经反复证明这些题真的会被问。

## 6. 第四层：Pro 进阶层

这一层主要在：

- `pro-jvm`

它解决的是：

- JIT
- 对象头 / Mark Word / 锁状态
- Safepoint / STW
- GC 日志阅读
- 堆外内存 / Direct Memory
- ClassLoader / Metaspace / 类卸载
- 调优参数思路
- 进阶案例

你可以把这一层理解成：

> 这是 JVM 的“深一层理解”。

它不一定是所有面试都必问，但一旦问到，会很拉开层次。

## 7. 最推荐的复习顺序

如果你从头到尾走一遍，我建议这个顺序：

1. 先过基础主线层
2. 再进入输出训练层
3. 然后看外部面经层做校验
4. 最后再补 Pro 进阶层

为什么不建议一上来就看 Pro？

因为如果基础主线不稳，JIT、Direct Memory、Metaspace 这些只会让你越学越碎。

## 8. 基础版什么时候算过线

你至少要做到：

- 能 1 分钟整体讲 JVM
- 能说清堆、栈、方法区
- 能讲可达性分析、分代、Full GC
- 能讲类加载和双亲委派
- 能讲 `volatile` 为什么不能保证 `i++`
- 能区分 OOM、Full GC、CPU 飙高

做到这些，基础版就基本过线了。

## 9. Pro 版什么时候值得开始补

满足下面这些情况时，就值得上 Pro：

1. 基础主线已经能讲顺
2. 一面常规 JVM 题已经不太慌
3. 你想准备更深一点的二面 / 社招 / 高要求面试
4. 你希望能把 JVM 和真实线上问题联系得更自然

换句话说：

> Pro 版不是替代基础版，而是建立在基础版已经稳住的前提上。

## 10. Pro 版最值的进入顺序

如果只按收益排，我建议：

1. `jvm-jit-note.md`
2. `jvm-gc-log-reading.md`
3. `jvm-direct-memory-note.md`
4. `jvm-classloader-metaspace-advanced.md`
5. `jvm-object-header-lock-note.md`
6. `jvm-safepoint-stw-note.md`
7. `jvm-tuning-parameters-note.md`
8. `jvm-advanced-case-study.md`

为什么这么排：

- JIT、GC 日志、Direct Memory、Metaspace 更常和面试深问、性能场景联系起来
- 对象头、Safepoint 会更偏机制理解
- 案例放最后，是为了把前面的知识重新压回场景里

## 11. 如果你时间不多，怎么走最划算

### 情况一：只剩 3 到 5 天

建议：

1. 基础主线层只看最核心几篇
2. `mock-and-oral` 优先
3. `interview-experience` 做校验
4. Pro 只看 JIT、GC 日志、Direct Memory、Metaspace

### 情况二：只剩 1 到 2 天

建议：

1. 看 `jvm-final-review.md`
2. 看 `mock-and-oral/jvm-cheatsheet-one-page.md`
3. 做 `mock-and-oral/jvm-final-mock-paper.md`
4. Pro 只扫一遍最感兴趣的 2 到 3 篇

### 情况三：面试前最后 1 小时

建议：

1. 看 `mock-and-oral/jvm-cheatsheet-one-page.md`
2. 看 `mock-and-oral/jvm-last-day-revision.md`
3. 看自己最容易错的那几道题

## 12. 怎么判断自己现在在哪一层

你可以简单自测：

- 如果你连 1 分钟都讲不顺，说明还在基础主线层
- 如果你知道知识点，但开口容易断，说明该重练输出训练层
- 如果你会答常规题，但怕真实面试问法，说明该看外部面经层
- 如果你常规题稳了，想拉开层次，说明可以进入 Pro 层

## 13. 最后的路线总结

可以记成一句话：

> 先把 JVM 主线学会，再把它练到能说出来，再用公开面经验证高频方向，最后进入 Pro 版把理解再往深处推进。

## 14. 一句话收尾

> JVM 从基础到 Pro 的关键，不是文档越多越好，而是每一层都知道自己在解决什么问题，再往下一层走。
