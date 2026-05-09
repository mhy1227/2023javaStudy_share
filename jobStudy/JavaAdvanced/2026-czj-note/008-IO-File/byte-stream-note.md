# 字节流基础笔记

## 1. 为什么先学字节流

IO 体系里最基础的一条主线就是：

- 字节流

因为很多更具体的流，往前追都能追到：

- `InputStream`
- `OutputStream`

所以先把字节流立住，后面看缓冲流、对象流、转换流会更顺。

## 2. 什么是字节流

字节流可以先理解成：

- 按字节读写数据的流

它更适合处理：

1. 图片
2. 视频
3. 音频
4. 压缩包
5. 各种二进制文件

当然，文本也能用字节流处理，但文本场景后面通常会更多联系到：

- 字符流

## 3. 字节流的两大父类

最核心的是：

1. `InputStream`
2. `OutputStream`

### InputStream

表示：

- 输入字节流
- 从外部读到程序里

### OutputStream

表示：

- 输出字节流
- 从程序写到外部

## 4. 最常见的文件字节流

最常见的两个类是：

1. `FileInputStream`
2. `FileOutputStream`

可以先记：

- 读文件 -> `FileInputStream`
- 写文件 -> `FileOutputStream`

## 5. FileInputStream 的基础例子

```java
FileInputStream fis = new FileInputStream("D:/test.txt");
int data = fis.read();
System.out.println(data);
fis.close();
```

这个例子可以先这样理解：

1. 打开文件输入流
2. 读一个字节
3. 最后关闭资源

这里读出来的 `data` 是：

- 字节值

不是直接就是“字符串文本”。

## 6. FileOutputStream 的基础例子

```java
FileOutputStream fos = new FileOutputStream("D:/out.txt");
fos.write(65);
fos.close();
```

这个例子里：

- `65` 对应字符 `A`

可以先理解成：

- 往文件里按字节写数据

## 7. read() 返回值要怎么理解

这个点很常见。

例如：

```java
int data = fis.read();
```

这里为什么返回 `int` 而不是 `byte`？

可以先粗记：

- 因为除了正常字节值，还要用 `-1` 表示读到文件末尾

所以面试里如果问到：

- 为什么 `read()` 返回 `int`

你可以从这个角度回答。

## 8. 用循环读文件

更常见写法是：

```java
FileInputStream fis = new FileInputStream("D:/test.txt");
int data;
while ((data = fis.read()) != -1) {
    System.out.println(data);
}
fis.close();
```

这段代码的核心是：

- 不断读
- 读到 `-1` 为止

## 9. 用字节数组提升读取效率

一个字节一个字节地读太碎了，所以更常见还会这样写：

```java
FileInputStream fis = new FileInputStream("D:/test.txt");
byte[] buffer = new byte[1024];
int len;
while ((len = fis.read(buffer)) != -1) {
    System.out.println(len);
}
fis.close();
```

这里可以先理解成：

- 一次读一批字节

这样通常会更高效。

## 10. 字节流和文本处理的关系

字节流也能处理文本，但要注意：

- 它读出来本质是字节

如果直接处理中文、字符编码等问题，后面通常会更自然转到：

- 字符流
- 转换流

所以可以先记：

- 字节流更偏底层
- 字符流更偏文本友好

## 11. 为什么字节流总会和 close() 一起出现

因为流本质上通常关联着：

- 文件资源
- 系统资源

如果不及时关闭，可能会导致：

1. 资源泄漏
2. 文件占用
3. 后续读写异常

所以字节流这一章一定会和：

- 资源释放
- `finally`
- `try-with-resources`

联系起来。

## 12. 字节流这块面试里容易问什么

常见问题有：

1. 字节流和字符流的区别
2. `InputStream` 和 `OutputStream` 的作用
3. `FileInputStream` / `FileOutputStream` 的使用场景
4. `read()` 为什么返回 `int`
5. 为什么读写完要关闭流
6. 一个字节一个字节读和用缓冲数组读的区别

## 13. 当前阶段最容易混的点

1. 输入和输出方向不要搞反
2. `File` 不等于 `FileInputStream`
3. `read()` 返回的是字节值或 `-1`
4. 字节流和字符流不要混
5. 用完流通常要记得关闭

## 14. 当前阶段最该记住的结论

1. 字节流按字节读写数据
2. `InputStream` 负责输入，`OutputStream` 负责输出
3. `FileInputStream` / `FileOutputStream` 是最基础的文件字节流
4. `read()` 返回 `int` 是为了兼容 `-1`
5. 流用完通常要关闭

## 15. 一句话总结

字节流的核心主线就是：`InputStream / OutputStream + 文件读写 + read/write + 资源关闭`。
