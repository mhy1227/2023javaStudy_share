# IO 与 File 占位说明

## 1. 这一章准备讲什么

Java 里的 IO 不是单个类，而是一整套输入输出体系。

这一章最容易出现的问题是：

- 类名很多
- 流很多
- 一上来容易看乱

所以这里还是先按老办法：

1. 先看总览
2. 再看族谱
3. 再按主题一点点拆

## 2. 为什么这一章紧跟异常之后

因为 IO 这块和异常天然联系很强。

最典型的就是：

- `IOException`
- 资源关闭
- `finally`
- `try-with-resources`

也就是说，异常那一章刚补完，接 IO 是最顺的。

## 3. 这一章后面准备继续补什么

建议后续顺序：

1. IO 族谱
2. `File` 基础
3. 字节流
4. 字符流
5. 缓冲流
6. 转换流
7. 对象流
8. 打印流
9. `try-with-resources`
10. 常见 IO 面试高频

另外，如果项目里涉及文件上传、分块上传、断点续传、文件合并这类场景，可以继续看上传场景专项题库：

- [upload-project-io-questions/README.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/008-IO-File/upload-project-io-questions/README.md)

## 4. 一句话总结

IO 这一章的核心，不是背很多类名，而是先分清：什么是文件、什么是字节流、什么是字符流、什么是输入、什么是输出、什么场景该用哪一类流。
