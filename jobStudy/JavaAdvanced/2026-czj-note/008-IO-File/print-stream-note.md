# 打印流基础笔记

## 1. 为什么打印流也值得单独讲

因为平时最常见的一段代码就是：

```java
System.out.println("hello");
```

很多人一直在用，但并不会立刻把它和：

- 打印流

联系起来。

所以这一块虽然不算特别难，但非常适合补成一篇单独笔记。

## 2. 什么是打印流

打印流可以先理解成：

- 更方便输出内容的一类流

最常见的是：

1. `PrintStream`
2. `PrintWriter`

它们最大的特点可以先粗记成：

- 输出文本更方便

## 3. PrintStream 是什么

`PrintStream` 最常见的例子就是：

- `System.out`

也就是说，平时写的：

```java
System.out.println("hello");
```

背后就和打印流强相关。

它常见的输出方法有：

1. `print()`
2. `println()`

## 4. PrintWriter 是什么

`PrintWriter` 也很常见，它更偏：

- 方便地输出字符 / 文本内容

示例：

```java
PrintWriter pw = new PrintWriter("D:/out.txt");
pw.println("hello");
pw.println("world");
pw.close();
```

这里可以先理解成：

- 直接把文本内容打印到文件里

## 5. 打印流和普通输出流有什么区别

这个点很容易被问。

可以先这样理解：

### 普通输出流

- 更偏底层写数据

### 打印流

- 更偏方便地打印文本和常见类型

也就是说，打印流的核心优势通常不是“能力完全不同”，而是：

- 用起来更顺手

## 6. 一个最常见的例子

```java
PrintStream ps = new PrintStream("D:/out.txt");
ps.println("name=Tom");
ps.println(18);
ps.close();
```

这个例子说明：

- 你可以很方便地把各种值打印到目标输出位置

## 7. PrintStream 和 PrintWriter 怎么粗分

当前阶段先不用死抠很细。

先有个感觉：

### PrintStream

- 更早期、和字节输出流关系更近

### PrintWriter

- 更偏字符文本输出

所以如果题目强调：

- 文本输出
- 字符输出

通常会更容易联想到：

- `PrintWriter`

## 8. 打印流为什么和面试有关系

因为它经常会被作为：

- IO 体系补充点

来问。

常见问法：

1. `System.out` 属于什么
2. `PrintStream` 和普通输出流有什么区别
3. `print()` 和 `println()` 的区别
4. `PrintWriter` 是做什么的

## 9. 当前阶段最容易混的点

1. `System.out` 和打印流有关
2. 打印流不是另一套完全独立体系
3. 打印流更强调方便输出
4. `PrintStream` 和 `PrintWriter` 都属于打印流家族

## 10. 当前阶段最该记住的结论

1. 打印流的核心价值是输出方便
2. `PrintStream` 和 `PrintWriter` 是最常见的两个类
3. `System.out` 背后和 `PrintStream` 强相关
4. 打印流常用于文本和控制台输出场景

## 11. 一句话总结

打印流最核心的特点，不是“会不会输出”，而是“让输出这件事变得更方便”。
