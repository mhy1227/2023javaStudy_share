# 异常体系占位说明

## 1. 这一章准备讲什么

Java 异常这一章，核心不是只背几个类名，而是先分清：

- `Throwable`
- `Error`
- `Exception`
- `RuntimeException`
- checked exception
- unchecked exception

也就是说，这一章最容易混的不是语法，而是：

- 异常体系结构
- 不同异常该怎么理解
- 哪些要处理，哪些通常不处理

## 2. 为什么先从族谱开始

因为异常这块如果一上来就讲：

- `try-catch-finally`
- `throw`
- `throws`

很多时候会变成“会写语法，但体系是乱的”。

所以这里先按老办法：

1. 先看族谱
2. 再看分类
3. 再看处理方式
4. 最后再看面试高频点

## 3. 这一章后面准备继续补什么

建议后续顺序：

1. 异常族谱
2. 常见异常例子
3. checked 和 unchecked
4. `throw` 和 `throws`
5. `final`、`finally`、`finalize`
6. `try-catch-finally`
7. 常见运行时异常
8. 面试高频问题
9. 自定义异常

## 4. 一句话总结

异常这一章，第一步先把“谁是谁、谁归谁管、哪些通常要处理”理清楚，后面再去看具体语法和面试题。
