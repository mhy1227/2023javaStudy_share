# 异常高频面试题

## 1. 这一份是干什么的

前面的文档已经把：

- 族谱
- 例子
- checked / unchecked
- `throw` / `throws`
- `final` / `finally` / `finalize`

这些基础结构铺开了。

这一份再单独补的是：

- 面试里最容易直接问出来的高频题

也就是把异常这章从“会看笔记”变成：

- 会回答

## 2. 异常这块高频到底在问什么

从牛客面经和 Java 讨论里看，异常这块高频问题比较集中，不是散的。

最核心就是这几类：

1. `Throwable`、`Error`、`Exception` 的关系
2. checked exception 和 unchecked exception 的区别
3. `throw` 和 `throws` 的区别
4. `try-catch-finally` 的执行顺序
5. `try` / `catch` 里有 `return`，`finally` 会怎样
6. `final`、`finally`、`finalize` 的区别
7. 常见运行时异常举例
8. `OOM` 和 `StackOverflowError`
9. 自定义异常什么时候用

## 3. 第一梯队：几乎必问

### 3.1 Throwable、Error、Exception 的关系

回答主线：

- `Throwable` 是顶层父类
- 它下面分成 `Error` 和 `Exception`
- `Exception` 是日常开发里异常处理的主线
- `Error` 更偏 JVM 或系统级严重问题

### 3.2 checked 和 unchecked 的区别

回答主线：

- checked exception 编译期通常要求处理或声明
- unchecked exception 通常是 `RuntimeException` 这一支
- checked 更偏外部资源失败
- unchecked 更偏代码逻辑和边界问题

### 3.3 throw 和 throws 的区别

回答主线：

- `throw` 是方法体内主动抛异常对象
- `throws` 是方法签名上声明可能抛哪些异常类型

### 3.4 final、finally、finalize 的区别

回答主线：

- `final` 是修饰符
- `finally` 是异常处理代码块
- `finalize` 是旧的回收清理方法，现在不推荐依赖

## 4. 第二梯队：非常爱追问

### 4.1 finally 一定会执行吗

更稳的答法：

- 正常控制流下通常会执行
- 但极端情况下不能说绝对 100%

### 4.2 try 里有 return，finally 还会执行吗

答案：

- 通常会

### 4.3 finally 里有 return 会怎样

答案：

- 会覆盖前面的返回结果

这也是为什么开发里通常不建议这么写。

### 4.4 能不能直接 catch Exception

更稳的答法：

- 不是绝对不能
- 但不能一上来就粗暴兜底
- 能按具体异常处理时尽量具体

## 5. 第三梯队：常作为延伸问题

### 5.1 常见运行时异常有哪些

最常举的例子：

1. `NullPointerException`
2. `IndexOutOfBoundsException`
3. `ClassCastException`
4. `ArithmeticException`
5. `NumberFormatException`

### 5.2 OOM 和 StackOverflowError 属于什么

回答主线：

- 它们属于 `Error`
- 不是普通业务异常处理主线

### 5.3 什么时候自定义异常

回答主线：

- 当通用异常类表达不了业务语义时
- 比如库存不足、订单状态非法、用户未登录

### 5.4 为什么不能乱吞异常

回答主线：

- 吞掉异常会导致排查困难
- 丢失上下文
- 还可能让上层误以为操作成功

## 6. 面试里最容易出的组合题

异常这块经常不是单点问，而是连着问。

例如：

1. `throw` 和 `throws` 区别
2. checked 和 unchecked 区别
3. 再追问 `try-catch-finally`
4. 最后追问 `final`、`finally`、`finalize`

所以复习时不要把这些点完全拆开记，要把它们串成一条线。

## 7. 如果只剩一轮时间，优先背什么

建议优先级：

1. `throw` 和 `throws`
2. checked 和 unchecked
3. `final`、`finally`、`finalize`
4. `try-catch-finally` 执行顺序
5. 常见运行时异常举例

## 8. 一段比较稳的总回答

可以这样答：

Java 异常这块我一般先按体系理解，`Throwable` 下面分 `Error` 和 `Exception`，其中 `Exception` 是平时开发里的主线。再往下，`RuntimeException` 通常属于 unchecked exception，像空指针、越界、数字转换失败这些都比较常见；而 `IOException`、`SQLException` 这类通常属于 checked exception，编译期一般要求处理或声明。语法上高频点主要是 `throw` 和 `throws` 的区别，以及 `try-catch-finally` 的执行顺序，尤其是 `return` 和 `finally` 的关系。另外 `final`、`finally`、`finalize` 也是经典高频混淆题。

## 9. 当前阶段最该记住的结论

1. 异常高频点并不散，主要就集中在少数几类
2. `throw` / `throws`、checked / unchecked、`final` / `finally` / `finalize` 都很高频
3. `try-catch-finally + return` 是特别爱追问的组合题
4. 运行时异常例子和 `Error` 场景也要能顺手举出来

## 10. 一句话总结

异常这一章的高频面试题，核心不是背特别多，而是把几组经典混淆点讲顺、举出例子、说清执行顺序。

## 11. 外部参考

1. 牛客：40道Java基础常见面试题及详细答案  
   https://www.nowcoder.com/discuss/353159104325689344
2. 牛客：java面试  
   https://www.nowcoder.com/discuss/353148586907082752
3. 牛客：java基础高频面试题  
   https://www.nowcoder.com/discuss/498248327440379904
4. 牛客：Keep校招JAVA面经  
   https://www.nowcoder.com/discuss/353159005688242176
5. 牛客：一天吃透Java面试八股文  
   https://www.nowcoder.com/discuss/521478358517940224
6. 牛客：真实面试题整理  
   https://www.nowcoder.com/discuss/739426350301188096
7. LeetCode：Exception Handling in Java  
   https://leetcode.com/discuss/general-discussion/147486/exception-handling-in-java/
8. LeetCode：Most Common Interview Question asked related to Exception Handling in Java  
   https://leetcode.com/discuss/post/4430844/Most-Common-Interview-Question-asked-related-to-Exception-Handling-in-Java/
