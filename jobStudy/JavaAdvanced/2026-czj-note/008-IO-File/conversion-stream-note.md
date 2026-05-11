# 转换流基础笔记

## 1. 为什么还要有转换流

前面已经有：

- 字节流
- 字符流

那为什么还要再补一类：

- 转换流

因为实际开发里，很多数据最开始是：

- 字节

但你最后想处理的是：

- 字符
- 文本

这时候就需要一座桥，把：

- 字节流
- 字符流

连起来。

所以可以先粗记：

- 转换流就是桥梁

## 2. 什么是转换流

转换流可以先理解成：

- 在字节流和字符流之间做转换的流

最常见的两个类是：

1. `InputStreamReader`
2. `OutputStreamWriter`

## 3. InputStreamReader 是什么

`InputStreamReader` 可以先理解成：

- 把字节输入流转成字符输入流

也就是说，它更像：

- 字节流进来
- 按字符方式读出来

最常见例子：

```java
InputStreamReader isr =
        new InputStreamReader(new FileInputStream("D:/test.txt"));
int ch;
while ((ch = isr.read()) != -1) {
    System.out.print((char) ch);
}
isr.close();
```

这个例子里：

1. 底层还是文件字节输入
2. 但你上层按字符在读

## 4. OutputStreamWriter 是什么

`OutputStreamWriter` 可以先理解成：

- 把字符输出流写成底层字节输出

最常见例子：

```java
OutputStreamWriter osw =
        new OutputStreamWriter(new FileOutputStream("D:/out.txt"));
osw.write("hello");
osw.close();
```

这个例子里：

- 你写的是字符内容
- 最后底层还是通过字节流写出去

## 5. 转换流和编码为什么总绑在一起

这个点非常重要。

因为：

- 字节和字符之间的转换

本质上就离不开：

- 编码规则

也就是说，转换流后面经常会和：

- UTF-8
- GBK

这些编码概念放在一起讲。

## 6. 指定编码的例子

例如：

```java
InputStreamReader isr =
        new InputStreamReader(new FileInputStream("D:/test.txt"), "UTF-8");
```

或者：

```java
OutputStreamWriter osw =
        new OutputStreamWriter(new FileOutputStream("D:/out.txt"), "UTF-8");
```

这里可以先理解成：

- 你明确告诉 Java，用什么编码把字节和字符对应起来

## 7. 为什么不直接用 FileReader / FileWriter

这个问题很常见。

可以先这样理解：

### FileReader / FileWriter

- 更直接
- 更像默认方式处理文本

### InputStreamReader / OutputStreamWriter

- 更灵活
- 更适合需要明确控制编码的场景

所以当题目里强调：

- 编码
- 字节到字符的转换

就更容易想到：

- 转换流

## 8. 转换流常和谁一起用

非常常见的一组组合是：

```java
BufferedReader br =
        new BufferedReader(
                new InputStreamReader(new FileInputStream("D:/test.txt"), "UTF-8"));
```

这个组合可以先理解成：

1. 底层文件字节输入
2. 转换成字符流
3. 再套一层缓冲流增强

这类写法在真实代码里很常见。

## 9. 转换流这块面试里容易问什么

常见问题有：

1. 转换流是做什么的
2. `InputStreamReader` 和 `OutputStreamWriter` 的作用
3. 为什么转换流和编码有关系
4. `FileReader` 和 `InputStreamReader` 的区别
5. 为什么会出现乱码问题

## 10. 当前阶段最容易混的点

1. 转换流不是普通基础流
2. 它的核心职责是“字节和字符之间搭桥”
3. `InputStreamReader` 是字节转字符
4. `OutputStreamWriter` 是字符转字节
5. 转换流经常和编码一起出现

## 11. 当前阶段最该记住的结论

1. 转换流负责连接字节流和字符流
2. `InputStreamReader` 和 `OutputStreamWriter` 是最核心的两个类
3. 转换流和字符编码关系非常紧
4. 需要控制编码时，转换流通常比 `FileReader` / `FileWriter` 更自然

## 12. 一句话总结

转换流最核心的意义，就是在“字节”和“字符”之间搭桥，并把编码问题纳入控制范围。
