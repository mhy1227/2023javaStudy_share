# 字符流基础笔记

## 1. 为什么要学字符流

前面已经补了：

- 字节流

但如果处理的是：

- 文本
- 字符
- 中文

只靠字节流去理解就容易不够顺。

所以 IO 这一章里，字符流是另一条非常重要的主线。

## 2. 什么是字符流

字符流可以先理解成：

- 按字符读写数据的流

它更适合处理：

1. 文本文件
2. 配置文件
3. 日志文件
4. 普通字符串内容

所以可以先粗记：

- 字节流更偏二进制
- 字符流更偏文本

## 3. 字符流的两大父类

最核心的是：

1. `Reader`
2. `Writer`

### Reader

表示：

- 输入字符流
- 从外部把字符读进程序

### Writer

表示：

- 输出字符流
- 从程序把字符写出去

## 4. 最常见的文件字符流

最常见的两个类是：

1. `FileReader`
2. `FileWriter`

可以先记：

- 读文本文件 -> `FileReader`
- 写文本文件 -> `FileWriter`

## 5. FileReader 的基础例子

```java
FileReader fr = new FileReader("D:/test.txt");
int ch = fr.read();
System.out.println(ch);
fr.close();
```

这里可以先理解成：

1. 打开字符输入流
2. 读一个字符
3. 最后关闭资源

## 6. FileWriter 的基础例子

```java
FileWriter fw = new FileWriter("D:/out.txt");
fw.write("hello");
fw.close();
```

这个例子可以先理解成：

- 直接按字符把文本写到文件里

所以在处理纯文本时，它通常比字节流更直观。

## 7. read() 返回值怎么理解

字符流里的：

```java
int ch = fr.read();
```

也通常返回：

- `int`

原因和字节流类似，主要也是为了：

- 用 `-1` 表示读到末尾

## 8. 循环读取字符

更常见写法是：

```java
FileReader fr = new FileReader("D:/test.txt");
int ch;
while ((ch = fr.read()) != -1) {
    System.out.print((char) ch);
}
fr.close();
```

这里重点是：

1. 不断读取
2. 读到 `-1` 为止
3. 读出来的内容可以转成 `char`

## 9. 用字符数组提升效率

和字节流一样，字符流也可以一次读一批：

```java
FileReader fr = new FileReader("D:/test.txt");
char[] buffer = new char[1024];
int len;
while ((len = fr.read(buffer)) != -1) {
    System.out.println(len);
}
fr.close();
```

可以先理解成：

- 一次读一段字符

这通常比一个字符一个字符读更高效。

## 10. 字符流和字节流怎么区分

这个点特别容易被问。

可以先这样记：

### 字节流

- 处理二进制数据更自然

### 字符流

- 处理文本更自然

如果题目是：

- 图片
- 视频
- 压缩包

优先更容易想到：

- 字节流

如果题目是：

- 文本
- 日志
- 配置文件

优先更容易想到：

- 字符流

## 11. 为什么字符流处理文本更自然

因为文本本来就是“字符语义”的内容。

所以在写：

- 文本读取
- 文本输出
- 按行处理

这种代码时，字符流通常会更顺手。

当然，后面还会继续遇到：

- 编码问题
- 转换流

所以字符流并不是整个文本处理的终点，只是更自然的入口。

## 12. 字符流这块面试里容易问什么

常见问题有：

1. 字节流和字符流的区别
2. `Reader` 和 `Writer` 的作用
3. `FileReader` / `FileWriter` 适合什么场景
4. 为什么字符流也要 `close()`
5. 一个字符一个字符读和用字符数组读的区别

## 13. 当前阶段最容易混的点

1. `Reader` 和 `InputStream` 不是一回事
2. `Writer` 和 `OutputStream` 不是一回事
3. 字节流和字符流的使用场景不要混
4. 文本处理更自然想到字符流
5. 字符流也要记得关闭

## 14. 当前阶段最该记住的结论

1. 字符流按字符读写数据
2. `Reader` 负责读字符，`Writer` 负责写字符
3. `FileReader` / `FileWriter` 很适合处理文本文件
4. 读写完字符流也通常要关闭
5. 文本处理时，字符流通常比字节流更直观

## 15. 一句话总结

字符流的核心主线就是：`Reader / Writer + 文本处理 + read/write + 资源关闭`。
