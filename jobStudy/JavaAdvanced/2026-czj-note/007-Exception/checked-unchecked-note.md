# checked 和 unchecked

## 1. 为什么这个点一定要单独拎出来

异常这一章里，最容易混的高频问题之一就是：

- checked exception 和 unchecked exception 到底怎么区分

很多人会背：

- `RuntimeException` 是运行时异常
- `IOException` 是受检异常

但一追问：

- 为什么它们不一样
- 编译期和运行期分别是什么意思
- 平时开发里怎么看待这两类异常

就容易讲乱。

所以这个点必须单独梳理。

## 2. 先说最短结论

可以先这样记：

### checked exception

- 编译期通常要求你处理或声明抛出

### unchecked exception

- 编译期通常不强制你显式处理

这就是最核心的区别。

## 3. checked exception 是什么

checked exception 通常可以先理解成：

- 编译器要求你正面面对的异常

也就是说，如果某段代码可能抛出这类异常，编译器通常不会让你直接不管。

你一般要么：

1. `try-catch`
2. `throws`

常见例子：

- `IOException`
- `SQLException`
- `ClassNotFoundException`

## 4. unchecked exception 是什么

unchecked exception 通常可以先理解成：

- 编译器不强制你显式处理的异常

它们最典型的主线是：

- `RuntimeException`

所以很多时候也会直接把 unchecked exception 理解成：

- 运行时异常这一支

常见例子：

- `NullPointerException`
- `IndexOutOfBoundsException`
- `ArithmeticException`
- `NumberFormatException`
- `ClassCastException`

## 5. 它们和族谱怎么对应

可以这样对应：

```text
Throwable
├─ Error
└─ Exception
   ├─ RuntimeException        -> unchecked exception
   └─ 其他很多 Exception      -> checked exception
```

先抓住这条主线最重要。

## 6. 一个最直观的代码区别

### 6.1 checked exception 例子

```java
public void readFile() throws IOException {
    FileInputStream fis = new FileInputStream("D:/test.txt");
}
```

这个例子里：

- 方法签名里要写 `throws IOException`

否则通常编译不过。

### 6.2 unchecked exception 例子

```java
public void test() {
    String name = null;
    System.out.println(name.length());
}
```

这个例子里：

- 代码能编译
- 但运行时会空指针

这就是两类异常非常直观的差别。

## 7. 为什么会有这种区分

可以粗理解成：

### checked exception

- 更偏外部资源和不可忽视的问题

例如：

- 文件不存在
- 数据库访问失败
- 类加载失败

编译器希望你：

- 明确处理
- 或者至少明确声明“我这里可能抛”

### unchecked exception

- 更偏程序逻辑、边界、参数处理问题

例如：

- 空指针
- 越界
- 类型转换失败

这类问题更多说明：

- 代码本身写得不够稳

## 8. 开发里一般怎么理解这两类异常

### checked exception

更像：

- 业务代码必须面对的外部失败

所以常见处理方式是：

- 记录日志
- 包装异常
- 向上抛出

### unchecked exception

更像：

- 代码写法或输入边界出了问题

所以更常见的思路是：

- 提前校验
- 判空
- 做边界保护

而不是等它真的抛出来再“补救”。

## 9. 面试里怎么答更稳

可以这样答：

checked exception 和 unchecked exception 的核心区别在于编译器是否强制处理。checked exception 一般要求你显式 `try-catch` 或 `throws`，常见于 `IOException`、`SQLException` 这类外部资源操作；unchecked exception 通常是 `RuntimeException` 这一支，比如空指针、越界、数字转换失败，它更偏代码逻辑和边界处理问题，编译器不强制你显式处理。

## 10. 当前阶段最容易混的点

最容易混的是：

1. `RuntimeException` 通常对应 unchecked exception
2. 不是所有 `Exception` 都是 checked exception
3. checked / unchecked 的关键不是“严不严重”
4. 它们的核心区别是编译期是否要求你处理

## 11. 当前阶段最该记住的结论

1. checked exception 通常要处理或声明
2. unchecked exception 通常是 `RuntimeException` 这一支
3. checked 更偏外部资源问题
4. unchecked 更偏代码逻辑和边界问题

## 12. 一句话总结

checked 和 unchecked 的核心不在于名字，而在于：编译器会不会强制你面对这个异常。
