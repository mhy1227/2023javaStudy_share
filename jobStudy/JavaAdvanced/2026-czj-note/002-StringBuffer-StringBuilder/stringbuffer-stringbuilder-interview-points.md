# StringBuffer 与 StringBuilder 高频面试点

## 1. String、StringBuffer、StringBuilder 的区别

这是最经典的问题。

建议回答模板：

- `String` 不可变
- `StringBuffer` 可变，线程安全
- `StringBuilder` 可变，非线程安全，但效率更高

## 2. 为什么 StringBuilder 效率更高

核心原因：

- `String` 每次拼接可能产生新对象
- `StringBuilder` 通常在原对象基础上追加内容

所以在频繁修改字符串的场景下：

- `StringBuilder` 更高效

## 3. 为什么 StringBuffer 线程安全

当前阶段简单记就够了：

- `StringBuffer` 的很多方法带同步控制
- 所以多线程下更安全

但代价是：

- 性能一般低于 `StringBuilder`

## 4. 什么时候用 String，什么时候用 StringBuilder

### 用 String

- 字符串内容基本不改
- 只是保存、展示、传递

### 用 StringBuilder

- 单线程下频繁拼接
- 循环中不断追加字符串

### 用 StringBuffer

- 多线程环境下确实需要可变字符串

## 5. 为什么循环里不建议总用 `+`

例如：

```java
String s = "";
for (int i = 0; i < 1000; i++) {
    s += i;
}
```

问题在于：

- 中间对象太多
- 性能较差

更好的写法：

```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);
}
String result = sb.toString();
```

## 6. `append()` 和 `toString()` 为什么重要

在实际使用中，最常见的模式就是：

1. 用 `append()` 构造内容
2. 最后用 `toString()` 转回普通字符串

例如：

```java
StringBuilder sb = new StringBuilder();
sb.append("name=").append("Tom").append(", age=").append(18);
String result = sb.toString();
```

## 7. `length()` 和 `capacity()` 的区别

### `length()`

- 当前字符个数

### `capacity()`

- 当前底层能容纳的容量

这个点常用来考你是否知道：

- 可变字符串底层是带容量概念的

## 8. `StringBuilder` 是否线程安全

答案：

- 不是

如果面试官继续问：

为什么很多场景还推荐它？

可以答：

- 大多数日常拼接发生在单线程环境
- 单线程下它效率更高

## 9. 高频易错点

### 易错点 1

以为 `StringBuilder` 和 `String` 一样不可变。

其实不是。

### 易错点 2

忘记最终转回 `String`。

### 易错点 3

把线程安全和效率关系说反。

正确关系是：

- `StringBuffer` 更安全
- `StringBuilder` 一般更快

## 10. 面试时的最简答题模板

### 问：String 和 StringBuilder 区别

答：

- `String` 不可变
- `StringBuilder` 可变
- 频繁拼接时 `StringBuilder` 更高效

### 问：StringBuffer 和 StringBuilder 区别

答：

- `StringBuffer` 线程安全
- `StringBuilder` 非线程安全但效率更高

### 问：什么时候用 StringBuilder

答：

- 在循环拼接、频繁修改字符串时使用

## 11. 一句话总结

面试中讲 `StringBuffer` 和 `StringBuilder`，关键不是背定义，而是讲清：

- 可变还是不可变
- 是否线程安全
- 什么场景下该用谁
