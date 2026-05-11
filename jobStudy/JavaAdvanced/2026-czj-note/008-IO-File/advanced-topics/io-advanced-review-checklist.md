# IO 补充专题考前复盘 Checklist

## 1. 这一份怎么用

这一份不是长篇笔记，而是 `008-IO-File/advanced-topics` 这一层的考前压缩复盘清单。

适合用法：

- 面试前最后 10 到 15 分钟快速过一遍
- 检查自己哪些补充点还答不顺
- 复盘“主线、关键词、场景口径”

复习时建议每块只问自己四个问题：

- 这一块核心在讲什么？
- 最值得记的关键词是什么？
- 面试最可能怎么问？
- 我会怎么一句话答出来？

## 2. `NIO` 快速复盘

主线：

- `NIO` 更常围绕 `Buffer`、`Channel`、`Path`、`Files` 来讲

必须记住：

- `BIO` 更偏传统流模型
- `NIO` 更偏缓冲区和通道
- `Buffer` 是缓冲区
- `Channel` 是传输通道
- `Path` 是路径表示
- `Files` 是围绕 `Path` 的工具方法入口

最容易错：

- 一上来把自己带进 `Selector`、多路复用、Netty 太深
- 只背类名，讲不清 `Buffer` 和 `Channel` 的关系

面试怎么说：

- `NIO` 和传统 IO 最大的差异在于组织方式不同，传统 IO 更常围绕流，`NIO` 更常围绕 `Buffer` 和 `Channel`，另外 `Path` 和 `Files` 也是很常见的一组入口。

## 3. 序列化补充快速复盘

主线：

- 不是再讲对象流怎么用，而是在讲序列化规则和边界

必须记住：

- `serialVersionUID` 和类版本兼容有关
- `transient` 字段默认不参与序列化
- `static` 字段通常也不属于对象实例序列化内容
- `Serializable` 是默认序列化常见前提
- 反序列化失败常和类结构变化、版本不一致有关

最容易错：

- 只会背对象流，不会讲 `serialVersionUID`
- 不知道哪些字段不会被序列化
- 一问反序列化失败就完全没思路

面试怎么说：

- 序列化补充里最常见的追问就是 `serialVersionUID`、`transient` 和哪些字段不会被序列化，本质上都是在问对象写出去和再读回来时的规则与边界。

## 4. IO 场景选型快速复盘

主线：

- 看到场景以后，先判断是二进制、文本、编码转换、对象写出，还是资源管理

必须记住：

- 复制图片 -> 字节流
- 读文本 -> 字符流
- 按行读文本 -> `BufferedReader`
- 涉及编码 -> `InputStreamReader` / `OutputStreamWriter`
- 写对象 -> `ObjectOutputStream` / `ObjectInputStream`
- 强调资源关闭 -> `try-with-resources`

最容易错：

- 一看到 IO 就乱报类名
- 把图片复制答成字符流
- 说不清 `FileReader` 和 `InputStreamReader` 的区别
- 只会答“关资源”，不会提 `try-with-resources`

面试怎么说：

- IO 场景题不是背类名，而是看到题目以后快速判断：这是二进制处理、文本处理、编码转换、对象序列化，还是资源关闭问题。

## 5. `FileReader` 和 `InputStreamReader` 快速复盘

主线：

- 一个更像简单文本读取
- 一个更像字节到字符的桥接

必须记住：

- `FileReader`：简单读本地文本文件
- `InputStreamReader`：字节流转字符流
- 涉及编码时，`InputStreamReader` 更自然

最容易错：

- 把两者讲成完全一样
- 说不清为什么有时 `InputStreamReader` 更自然

## 6. `BufferedReader` 为什么常被追问

主线：

- 不只是缓冲，还因为它有 `readLine()`

必须记住：

- 文本处理里它很高频
- 按行读文本时很自然

最容易错：

- 只会说“更高效”，不会说“更顺手”

## 7. 序列化补充里最值得背的三句话

- `serialVersionUID` 和类版本兼容有关。
- `transient` 字段默认不参与序列化。
- `static` 字段通常不属于对象实例序列化内容。

## 8. IO 场景题里最值得背的三句话

- 图片复制通常先想到字节流。
- 文本读取通常先想到字符流或缓冲字符流。
- 涉及编码转换时，`InputStreamReader` 往往比 `FileReader` 更自然。

## 9. 考前最后五个总复盘点

- 我能不能用一句话区分 `BIO` 和 `NIO`？
- 我能不能说清 `Buffer` 和 `Channel` 的关系？
- 我知不知道 `serialVersionUID`、`transient`、`static` 在序列化里的位置？
- 我能不能看到场景以后立刻想到最自然的一组 IO 类？
- 我会不会把 IO 场景题答成“只背类名，不讲为什么”？

## 10. 最后一轮快问快答

- `BIO` 和 `NIO` 的粗区别是什么？
- `Buffer` 和 `Channel` 分别是做什么的？
- `Path` 和 `Files` 为什么常和 `NIO` 一起讲？
- 什么是 `serialVersionUID`？
- `transient` 是什么？
- 哪些字段通常不会被序列化？
- 为什么复制图片通常先想到字节流？
- 为什么按行读文本常提 `BufferedReader`？
- 为什么有时 `InputStreamReader` 比 `FileReader` 更自然？

