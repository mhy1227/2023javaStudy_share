# 异常体系族谱

## 1. 为什么异常也要先看族谱

异常这一章最容易出现的情况是：

- 会写 `try-catch`
- 但说不清 `Throwable`、`Error`、`Exception` 的关系

所以这里还是先用“族谱”的方式把大结构搭起来。

## 2. 先给一个最基础的异常族谱

```text
Throwable
├─ Error
└─ Exception
   ├─ RuntimeException
   └─ 其他非 RuntimeException 的异常
```

先抓住这条主线就够了。

## 3. Throwable 是什么

`Throwable` 是异常体系的最顶层父类。

也就是说：

- `Error`
- `Exception`

都属于：

- `Throwable`

所以可以先记：

- 只要是 Java 异常体系里常讲的这些，最上面都能追到 `Throwable`

## 4. Error 是什么

`Error` 通常表示：

- 更严重的问题

例如：

- JVM 或运行环境层面的严重错误

当前阶段先记这个感觉就够了：

- `Error` 一般不是普通业务代码去主动处理的主线

常见例子：

- `OutOfMemoryError`
- `StackOverflowError`

## 5. Exception 是什么

`Exception` 才是平时写 Java 代码时最常说的：

- 异常

也就是说，日常开发里常见的绝大多数“异常处理”讨论，重点通常都落在：

- `Exception`

这一支上。

## 6. Exception 下面最重要的分法

`Exception` 下面最重要的就是这两个方向：

1. `RuntimeException`
2. 非 `RuntimeException` 的其他异常

这个地方正好对应面试里常问的：

- checked exception
- unchecked exception

## 7. RuntimeException 是什么

`RuntimeException` 一般对应：

- 运行时异常

它常常表示：

- 代码运行过程中，因为逻辑、边界、参数等问题导致的异常

这一类通常也会被叫做：

- unchecked exception

也就是：

- 非受检异常

## 8. 常见 RuntimeException 例子

这些都很常见：

- `NullPointerException`
- `IndexOutOfBoundsException`
- `ArrayIndexOutOfBoundsException`
- `StringIndexOutOfBoundsException`
- `ClassCastException`
- `ArithmeticException`
- `NumberFormatException`

这类异常你在做题、写业务代码、写练习类时都会很常见。

## 9. 非 RuntimeException 的异常是什么

`Exception` 里除了 `RuntimeException` 这一支，剩下还有一些异常通常会被理解成：

- checked exception

也就是：

- 受检异常

这类异常在学习时最常见的印象是：

- 编译期会要求你显式处理或声明抛出

常见例子：

- `IOException`
- `SQLException`
- `ClassNotFoundException`

## 10. checked 和 unchecked 怎么粗记

可以先这样记：

### checked exception

- 更强调“编译期得面对它”

### unchecked exception

- 更强调“运行时暴露出来”

当前阶段先有这个感觉就够了，后面再专门展开。

## 11. 再给一个更详细一点的族谱

```text
Throwable
├─ Error
│  ├─ OutOfMemoryError
│  └─ StackOverflowError
│
└─ Exception
   ├─ RuntimeException
   │  ├─ NullPointerException
   │  ├─ IndexOutOfBoundsException
   │  ├─ ClassCastException
   │  ├─ ArithmeticException
   │  └─ NumberFormatException
   │
   └─ Checked Exception
      ├─ IOException
      ├─ SQLException
      └─ ClassNotFoundException
```

这张图不用一次全背，但结构要有印象。

## 12. 面试里最容易问哪几个点

异常体系这块最容易先被问到：

1. `Throwable`、`Error`、`Exception` 的关系
2. `Error` 和 `Exception` 的区别
3. checked 和 unchecked 的区别
4. `RuntimeException` 属于哪一类
5. 常见运行时异常有哪些

所以先把这几个点说顺，比一上来背一堆语法更重要。

## 13. 当前阶段最容易混的点

最容易混的是：

1. `Throwable` 是总父类
2. `Error` 不是普通业务异常处理主线
3. `Exception` 才是常规异常处理重点
4. `RuntimeException` 属于 `Exception`
5. `RuntimeException` 通常对应 unchecked exception

## 14. 当前阶段最该记住的结论

1. `Throwable` 是异常体系顶层父类
2. 它下面分成 `Error` 和 `Exception`
3. `Exception` 下面最重要的是 `RuntimeException`
4. `RuntimeException` 通常是 unchecked exception
5. 非 `RuntimeException` 的很多异常通常属于 checked exception

## 15. 一句话总结

Java 异常体系最核心的主线就是：`Throwable -> Error / Exception -> RuntimeException / checked exception`。
