# 文件上传项目 IO 追问题库

## 1. 这一目录是干什么的

这一目录专门收“文件上传类项目”在面试里可能被继续追问的 IO 相关问题。

它和前面 `008-IO-File` 主干内容的区别是：

- 主干更偏 Java IO 知识体系
- 这里更偏项目场景追问

也就是说，这一目录不是重新讲一遍流，而是把：

- 文件上传
- 分块上传
- 断点续传
- 秒传
- 文件合并
- 本地文件系统存储

这些场景下最容易被问到的 IO 问题单独收出来。

## 2. 为什么单独开子目录

如果你的项目里有文件上传模块，面试官通常不会只停留在：

- 字节流和字符流的区别
- `BufferedReader` 是什么

更常见的是顺着项目往下追：

- 上传文件为什么更偏字节流
- 分块文件怎么落盘
- 合并时怎么做 IO
- 为什么不能一次性读进内存
- `RandomAccessFile` 能不能用
- `NIO`、`FileChannel` 你了解多少

这些问题既和 IO 有关，又和项目设计强相关，所以单独开目录更清楚。

## 3. 当前目录索引

- [upload-project-io-possible-questions.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/008-IO-File/upload-project-io-questions/upload-project-io-possible-questions.md)
- [upload-project-io-answer-pack-0-1min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/008-IO-File/upload-project-io-questions/upload-project-io-answer-pack-0-1min.md)
- [upload-project-io-answer-pack-0-3min.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/008-IO-File/upload-project-io-questions/upload-project-io-answer-pack-0-3min.md)
- [upload-project-io-bonus-followups.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/008-IO-File/upload-project-io-questions/upload-project-io-bonus-followups.md)
- [upload-project-io-low-frequency-deep-questions.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/008-IO-File/upload-project-io-questions/upload-project-io-low-frequency-deep-questions.md)
- [upload-project-io-low-frequency-answer-samples.md](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/2026-czj-note/008-IO-File/upload-project-io-questions/upload-project-io-low-frequency-answer-samples.md)

## 4. 后续准备怎么补

建议按这个顺序往下补：

1. 先整理“可能会问的问题”
2. 再整理“每个问题的稳妥回答”
3. 再补“1 分钟项目型 IO 追问口语稿”

## 5. 一句话总结

这一目录是把 Java IO 从“知识点复习”切到“文件上传项目面试追问”。
