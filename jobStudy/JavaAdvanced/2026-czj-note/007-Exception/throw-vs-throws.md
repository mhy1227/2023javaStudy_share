# throw 和 throws

## 1. 为什么这个点特别容易混

因为它们长得太像了：

- `throw`
- `throws`

但它们不是一回事。

这个点在面试里非常高频，而且几乎每次都会被问到：

- `throw` 和 `throws` 有什么区别

## 2. 先说最短结论

可以先这样记：

### throw

- 在方法体里，真正把一个异常对象抛出去

### throws

- 写在方法声明上，表示这个方法可能抛出哪些异常

一句话：

- `throw` 是动作
- `throws` 是声明

## 3. throw 是什么

`throw` 是关键字，用来：

- 主动抛出一个异常对象

示例：

```java
if (age < 0) {
    throw new IllegalArgumentException("age can not be negative");
}
```

这里的含义就是：

- 我发现参数非法
- 所以主动抛一个异常出去

## 4. throws 是什么

`throws` 写在方法声明上，用来表示：

- 这个方法执行过程中可能抛出哪些异常

示例：

```java
public void readFile() throws IOException {
    FileInputStream fis = new FileInputStream("D:/test.txt");
}
```

这里的含义就是：

- 这个方法可能抛出 `IOException`
- 调用方要意识到这件事

## 5. 一个最直观的对比

### throw

```java
public void checkAge(int age) {
    if (age < 0) {
        throw new IllegalArgumentException("age error");
    }
}
```

特点：

- 写在方法体内部
- 后面跟的是异常对象

### throws

```java
public void readFile() throws IOException {
    FileInputStream fis = new FileInputStream("D:/test.txt");
}
```

特点：

- 写在方法签名后面
- 后面跟的是异常类型

## 6. 它们能不能一起出现

可以。

例如：

```java
public void test(String str) throws IOException {
    if (str == null) {
        throw new IllegalArgumentException("str is null");
    }
    FileInputStream fis = new FileInputStream("D:/test.txt");
}
```

这个例子里：

- `throws IOException` 是声明
- `throw new IllegalArgumentException(...)` 是主动抛出

所以它们不是互斥关系。

## 7. 面试里怎么解释更稳

可以这样答：

`throw` 是在方法内部主动抛出一个具体异常对象，强调的是“抛出动作”；`throws` 是写在方法声明上，表示这个方法可能抛出哪些异常类型，强调的是“对外声明”。前者后面跟对象，后者后面跟类型。

## 8. 什么时候更常用 throw

更常见场景是：

1. 参数校验失败
2. 业务规则不满足
3. 主动中断当前流程

例如：

- 用户年龄不能小于 0
- 订单状态不合法
- 方法参数不能为空

这时很常会主动：

- `throw new IllegalArgumentException(...)`
- `throw new RuntimeException(...)`

## 9. 什么时候更常用 throws

更常见场景是：

1. 方法里调用了可能抛 checked exception 的代码
2. 当前层不想处理，交给上层处理

例如：

- 文件读取
- 数据库访问
- 反射加载类

## 10. 当前阶段最容易混的点

最容易混的是：

1. `throw` 后面跟对象，不是类型
2. `throws` 后面跟类型，不是对象
3. `throw` 写在方法体里
4. `throws` 写在方法声明上
5. 两者可以同时存在

## 11. 再配一个更自然的业务例子

```java
public void register(String username) throws IOException {
    if (username == null || username.trim().isEmpty()) {
        throw new IllegalArgumentException("username is empty");
    }

    FileInputStream fis = new FileInputStream("D:/user.txt");
}
```

这里可以这样理解：

- 用户名为空，这是参数问题，所以主动 `throw`
- 读文件可能失败，这是资源问题，所以方法声明 `throws`

这个例子很适合面试时拿来讲。

## 12. 当前阶段最该记住的结论

1. `throw` 是抛出动作
2. `throws` 是方法声明
3. `throw` 后面跟异常对象
4. `throws` 后面跟异常类型
5. 两者经常会一起出现

## 13. 一句话总结

`throw` 和 `throws` 的区别很好记：一个在方法里真抛，一个在方法签名上先声明。
