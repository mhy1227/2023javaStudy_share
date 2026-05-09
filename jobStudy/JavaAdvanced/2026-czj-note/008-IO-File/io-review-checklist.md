# IO 复习清单

## 1. 第一轮先复习什么

建议先按这条线复习：

1. IO 族谱
2. `File`
3. 字节流
4. 字符流
5. 缓冲流
6. 转换流
7. 对象流
8. 打印流
9. `try-with-resources`
10. IO 高频面试题

## 2. IO 这一章最该先分清什么

至少要先分清：

1. `File` 不等于流
2. 字节流和字符流不是一回事
3. 输入和输出方向不要搞反
4. 缓冲流是增强层
5. 转换流和编码强相关

## 3. File 是否过关

至少要会：

1. `File` 是文件和目录路径的抽象表示
2. `exists()`、`isFile()`、`isDirectory()`
3. `getName()`、`getPath()`、`getAbsolutePath()`
4. `mkdir()` 和 `mkdirs()`
5. 创建 `File` 对象不代表目标一定存在

## 4. 字节流是否过关

至少要会：

1. `InputStream` 和 `OutputStream`
2. `FileInputStream` 和 `FileOutputStream`
3. `read()` 为什么返回 `int`
4. 一个字节一个字节读
5. 用 `byte[] buffer` 批量读取
6. 为什么流用完要关闭

## 5. 字符流是否过关

至少要会：

1. `Reader` 和 `Writer`
2. `FileReader` 和 `FileWriter`
3. 为什么文本处理更自然想到字符流
4. 用 `char[]` 做批量读取
5. 字符流和字节流的使用场景区别

## 6. 缓冲流是否过关

至少要会：

1. 为什么还要有缓冲流
2. `BufferedInputStream` / `BufferedOutputStream`
3. `BufferedReader` / `BufferedWriter`
4. `readLine()` 的作用
5. `newLine()` 的作用
6. 缓冲流和基础流是什么关系

## 7. 转换流是否过关

至少要会：

1. `InputStreamReader`
2. `OutputStreamWriter`
3. 转换流是在字节流和字符流之间搭桥
4. 转换流和编码问题为什么总绑在一起
5. 为什么有时比 `FileReader` / `FileWriter` 更自然

## 8. 对象流是否过关

至少要会：

1. `ObjectOutputStream`
2. `ObjectInputStream`
3. 什么是序列化和反序列化
4. 自定义对象为什么通常要实现 `Serializable`
5. 对象流和底层字节流是什么关系

## 9. 打印流是否过关

至少要会：

1. `PrintStream`
2. `PrintWriter`
3. `System.out` 和 `PrintStream` 的关系
4. 打印流的核心价值是“输出更方便”

## 10. 资源关闭是否过关

至少要会：

1. 为什么 IO 一定强调关闭资源
2. `finally` 方案和 `try-with-resources` 的区别
3. 为什么 `try-with-resources` 更推荐
4. 多个资源能否同时写进 `try-with-resources`
5. 它不是替代异常处理，而是自动关闭资源

## 11. 编码和乱码是否有感觉

至少要能说清：

1. 乱码通常和编码 / 解码规则不一致有关
2. 转换流经常和编码一起出现
3. 读取文本时如果编码不一致，就容易出问题

## 12. IO 这章的高频面试题是否过关

至少要能回答：

1. `File` 和流的区别
2. 字节流和字符流的区别
3. 缓冲流为什么存在
4. 转换流是做什么的
5. 为什么会出现乱码
6. 对象流和序列化是什么关系
7. `try-with-resources` 为什么更推荐
8. `System.out` 和哪类流有关

## 13. 如果面试只剩一轮复习时间

优先顺序：

1. `File` 和流的区别
2. 字节流和字符流的区别
3. 缓冲流
4. 转换流和编码
5. `try-with-resources`
6. 对象流和序列化

## 14. 当前阶段最容易混的点

1. `File` 不等于流
2. 文本处理到底该想到字节流还是字符流
3. 缓冲流是不是独立体系
4. 转换流和普通字符流的区别
5. `try-with-resources` 是不是等于不用处理异常
6. 对象流和打印流的使用场景

## 15. 一句话总结

IO 这一章复习到位的标志，不是类名背得多，而是你看到场景以后能快速判断：该想到 `File`、字节流、字符流、缓冲流、转换流、对象流，还是打印流。
