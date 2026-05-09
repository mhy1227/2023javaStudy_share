# 缓冲流基础笔记

## 1. 为什么还要学缓冲流

前面已经有：

- 字节流
- 字符流

那为什么还要再来一层：

- 缓冲流

因为基础流虽然能直接读写，但很多时候：

1. 读写太碎
2. 性能不够理想
3. 用起来不够方便

所以缓冲流可以先理解成：

- 对基础流的增强

## 2. 什么是缓冲流

缓冲流可以先理解成：

- 在基础流外面再包一层，提升读写效率和使用体验

最常见的有：

1. `BufferedInputStream`
2. `BufferedOutputStream`
3. `BufferedReader`
4. `BufferedWriter`

## 3. 它和基础流是什么关系

这个点非常重要。

不要把缓冲流理解成另一套平行体系。

更准确地说：

- 缓冲流通常是包在基础流外面的增强层

例如：

```java
BufferedInputStream bis =
        new BufferedInputStream(new FileInputStream("D:/test.txt"));
```

这里的关系是：

1. `FileInputStream` 负责文件字节输入
2. `BufferedInputStream` 在外面加缓冲

## 4. 字节缓冲流

### 4.1 BufferedInputStream

适合：

- 更高效地读取字节数据

示例：

```java
BufferedInputStream bis =
        new BufferedInputStream(new FileInputStream("D:/test.txt"));
int data;
while ((data = bis.read()) != -1) {
    System.out.println(data);
}
bis.close();
```

### 4.2 BufferedOutputStream

适合：

- 更高效地写出字节数据

示例：

```java
BufferedOutputStream bos =
        new BufferedOutputStream(new FileOutputStream("D:/out.txt"));
bos.write("hello".getBytes());
bos.close();
```

## 5. 字符缓冲流

### 5.1 BufferedReader

它很重要，因为它不只是缓冲，还常常和：

- 按行读文本

联系在一起。

示例：

```java
BufferedReader br =
        new BufferedReader(new FileReader("D:/test.txt"));
String line;
while ((line = br.readLine()) != null) {
    System.out.println(line);
}
br.close();
```

这里的重点是：

- `readLine()` 很常用

### 5.2 BufferedWriter

适合：

- 更方便地写文本

示例：

```java
BufferedWriter bw =
        new BufferedWriter(new FileWriter("D:/out.txt"));
bw.write("hello");
bw.newLine();
bw.write("world");
bw.close();
```

这里的重点是：

- `newLine()` 比手写换行更自然

## 6. 为什么缓冲流通常更常见

因为实际开发里，很少有人只满足于：

- 一个字节一个字节读
- 一个字符一个字符写

更常见的思路是：

- 用基础流打开资源
- 再用缓冲流包一层

这样通常更接近真实开发写法。

## 7. 缓冲流和性能怎么理解

当前阶段先粗记：

- 缓冲流通常能减少底层频繁读写带来的开销

所以它最大的价值通常是：

1. 提升效率
2. 提升使用便利性

## 8. 缓冲流这块面试里容易问什么

常见问题有：

1. 为什么要有缓冲流
2. 缓冲流和基础流是什么关系
3. `BufferedReader` 为什么常用
4. `readLine()` 是哪个类的方法
5. `BufferedWriter` 和 `newLine()` 的作用

## 9. 当前阶段最容易混的点

1. 缓冲流不是完全独立的新体系
2. 它通常要包在基础流外面
3. `BufferedReader` 和 `FileReader` 不一样
4. `readLine()` 是 `BufferedReader` 的高频方法
5. 最后关闭外层流通常就可以了

## 10. 当前阶段最该记住的结论

1. 缓冲流是基础流的增强
2. 字节缓冲流和字符缓冲流都很常见
3. `BufferedReader` / `BufferedWriter` 在文本处理里非常常用
4. `readLine()` 和 `newLine()` 是很高频的点
5. 缓冲流的核心价值是效率和便利性

## 11. 一句话总结

缓冲流最核心的作用，就是在基础流外面再包一层，让 IO 读写更高效、更顺手。
