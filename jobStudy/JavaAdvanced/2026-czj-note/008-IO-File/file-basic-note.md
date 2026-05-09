# File 基础笔记

## 1. 为什么先学 File

IO 这一章虽然重点是各种流，但真正开始写之前，通常先会碰到：

- 文件在哪里
- 路径怎么表示
- 目标是文件还是目录

所以 `File` 更像：

- IO 的入口认知

先把 `File` 理清楚，后面字节流、字符流会顺很多。

## 2. File 是什么

`File` 可以先理解成：

- 文件和目录路径的抽象表示

它并不是“真正负责读写内容的类”，而更像：

- 帮你描述一个文件
- 帮你描述一个目录
- 帮你做文件层面的判断和操作

所以要先记住：

- `File` 不等于流

## 3. 一个最基础的例子

```java
File file = new File("D:/test.txt");
System.out.println(file.getName());
System.out.println(file.getPath());
```

这里可以先理解成：

- 你创建了一个 `File` 对象
- 但不代表文件内容已经被读取

它更像是在内存里“描述这个路径”。

## 4. File 能做什么

当前阶段先记最常见这些：

1. 判断文件或目录是否存在
2. 判断是文件还是目录
3. 获取文件名、路径、绝对路径
4. 创建文件或目录
5. 删除文件或目录
6. 列出目录下内容

## 5. 最常见的方法

### 5.1 exists()

判断目标是否存在：

```java
File file = new File("D:/test.txt");
System.out.println(file.exists());
```

### 5.2 isFile() 和 isDirectory()

判断它是文件还是目录：

```java
File file = new File("D:/test.txt");
System.out.println(file.isFile());
System.out.println(file.isDirectory());
```

### 5.3 getName()、getPath()、getAbsolutePath()

获取文件名和路径：

```java
File file = new File("D:/test.txt");
System.out.println(file.getName());
System.out.println(file.getPath());
System.out.println(file.getAbsolutePath());
```

### 5.4 mkdir() 和 mkdirs()

创建目录：

```java
File dir = new File("D:/demo/test");
dir.mkdirs();
```

可以先粗记：

- `mkdir()` 更像创建单级目录
- `mkdirs()` 更像创建多级目录

### 5.5 createNewFile()

创建文件：

```java
File file = new File("D:/demo/test.txt");
file.createNewFile();
```

这个方法后面会和：

- `IOException`

联系起来。

### 5.6 delete()

删除文件或目录：

```java
File file = new File("D:/demo/test.txt");
file.delete();
```

## 6. File 和目录操作的一个例子

```java
File dir = new File("D:/demo");

if (!dir.exists()) {
    dir.mkdirs();
}

System.out.println(dir.getName());
System.out.println(dir.isDirectory());
```

这个例子更贴近实际使用方式：

- 先判断
- 再创建
- 再做后续操作

## 7. File 和读写内容是什么关系

这个点非常容易混。

要先明确：

- `File` 主要负责文件和路径层面的操作

而真正读写内容，通常还是靠：

1. 字节流
2. 字符流

所以不要把：

- `File`
- `FileInputStream`
- `FileReader`

混成一类。

## 8. 面试里 File 这块通常怎么问

比较常见的问法有：

1. `File` 是做什么的
2. `File` 能不能直接读写内容
3. `mkdir()` 和 `mkdirs()` 的区别
4. 如何判断是文件还是目录
5. `File` 和流是什么关系

## 9. 当前阶段最容易混的点

1. `File` 不等于流
2. 创建 `File` 对象不等于文件一定存在
3. 文件和目录判断不要混
4. `mkdir()` 和 `mkdirs()` 不一样
5. 文件内容读写不是 `File` 的主线职责

## 10. 当前阶段最该记住的结论

1. `File` 是文件和目录路径的抽象表示
2. `File` 主要做路径、存在性、类型、创建删除等操作
3. `File` 不负责真正的内容读写
4. 真正读写内容还要靠各种流

## 11. 一句话总结

`File` 的核心作用不是“读写内容”，而是“描述文件 / 目录并做文件层面的基础操作”。
