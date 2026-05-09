# IO 体系族谱

## 1. 为什么 IO 也要先看族谱

IO 这一章和集合、异常很像：

- 不是单个知识点
- 而是一整套体系

如果不先看结构，很容易出现这种情况：

- `InputStream` 见过
- `Reader` 见过
- `BufferedReader` 也见过
- 但不知道它们到底是什么关系

所以这里先用族谱把大结构理一遍。

## 2. 先说最短结论

可以先这样记：

1. `File` 负责表示文件和路径
2. 字节流负责处理二进制数据
3. 字符流负责处理文本字符
4. 输入流是往程序里读
5. 输出流是从程序里写出去

先记住这 5 句，后面就不容易乱。

## 3. File 是什么

`File` 可以先理解成：

- 文件和目录路径的抽象表示

它不是“真正读写内容的流”，而更像：

- 帮你表示一个文件
- 帮你表示一个目录
- 帮你做一些文件级操作

例如：

- 判断文件是否存在
- 获取文件名
- 创建目录

所以要先记住：

- `File` 不等于流

## 4. IO 体系最核心的大分法

最核心可以先分成两大类：

1. 字节流
2. 字符流

### 字节流

更适合处理：

- 图片
- 视频
- 音频
- 二进制文件

### 字符流

更适合处理：

- 文本
- 字符内容

## 5. 再按方向分：输入和输出

无论字节流还是字符流，都还会再分：

1. 输入
2. 输出

可以先这样理解：

### 输入

- 从外部读到程序里

### 输出

- 从程序写到外部

## 6. 一个基础版 IO 族谱

```text
IO 体系
├─ File
│
├─ 字节流
│  ├─ InputStream
│  └─ OutputStream
│
└─ 字符流
   ├─ Reader
   └─ Writer
```

这一版最基础，也最重要。

## 7. 一个更详细一点的族谱

```text
IO 体系
├─ File
│
├─ 字节流
│  ├─ InputStream
│  │  ├─ FileInputStream
│  │  ├─ BufferedInputStream
│  │  └─ ObjectInputStream
│  │
│  └─ OutputStream
│     ├─ FileOutputStream
│     ├─ BufferedOutputStream
│     ├─ ObjectOutputStream
│     └─ PrintStream
│
└─ 字符流
   ├─ Reader
   │  ├─ FileReader
   │  ├─ BufferedReader
   │  └─ InputStreamReader
   │
   └─ Writer
      ├─ FileWriter
      ├─ BufferedWriter
      ├─ OutputStreamWriter
      └─ PrintWriter
```

这张图不用一口气全背，但主线要有印象。

## 8. 为什么还会有缓冲流

因为基础流虽然能读写，但很多时候性能和使用体验不够好。

所以还会在外面再包一层：

- 缓冲流

例如：

- `BufferedInputStream`
- `BufferedOutputStream`
- `BufferedReader`
- `BufferedWriter`

可以先粗记：

- 缓冲流通常是对基础流的增强

## 9. 为什么还会有转换流

这个点以后也很重要。

转换流最核心是：

- 在字节流和字符流之间搭桥

最典型的就是：

- `InputStreamReader`
- `OutputStreamWriter`

这类流后面经常会和：

- 字符编码

一起出现。

## 10. 为什么还会有对象流

对象流更偏：

- 把对象写出去
- 或者把对象读回来

典型类：

- `ObjectInputStream`
- `ObjectOutputStream`

它和序列化会直接关联。

## 11. 为什么打印流也值得知道

打印流例如：

- `PrintStream`
- `PrintWriter`

它的特点是：

- 输出更方便
- 常和打印文本、日志类场景联系在一起

例如：

- `System.out` 背后就和打印流有关

## 12. IO 和异常的关系为什么特别紧

因为 IO 经常要面对：

- 文件不存在
- 读写失败
- 资源关闭

所以它天然会和：

- `IOException`
- `try-catch-finally`
- `try-with-resources`

绑在一起。

这也是为什么 IO 放在异常后面学最顺。

## 13. 当前阶段最容易混的点

最容易混的是：

1. `File` 不等于流
2. 字节流和字符流不要混
3. 输入和输出方向不要搞反
4. 缓冲流是增强，不是另一套平行体系
5. 转换流是桥梁，不是普通基础流

## 14. 当前阶段最该记住的结论

1. `File` 负责表示文件和路径
2. 字节流处理二进制
3. 字符流处理文本
4. 输入是读进来，输出是写出去
5. 缓冲流、转换流、对象流、打印流都是在基础流上的延伸

## 15. 一句话总结

IO 体系最核心的主线就是：`File + 字节流 / 字符流 + 输入 / 输出 + 各种增强流`。
