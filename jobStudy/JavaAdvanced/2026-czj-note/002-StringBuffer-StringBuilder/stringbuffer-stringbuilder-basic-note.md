# StringBuffer 与 StringBuilder 基础笔记

## 1. 为什么要学这一章

学完 `String` 之后，下一步很自然就是：

- `StringBuffer`
- `StringBuilder`

因为它们和 `String` 最大的区别在于：

- `String` 不可变
- `StringBuffer` 和 `StringBuilder` 可变

这两个类主要解决的问题是：

- 频繁拼接字符串时效率低

## 2. String 的问题是什么

例如：

```java
String s = "";
for (int i = 0; i < 10; i++) {
    s += i;
}
```

这样写的问题是：

- 每次拼接都可能生成新字符串对象
- 中间对象比较多
- 效率不高

所以当字符串内容需要频繁修改时，`String` 往往不是最合适的选择。

## 3. StringBuffer 和 StringBuilder 是什么

它们本质上都是：

- 可变字符串容器

也就是说：

- 里面的字符内容可以直接追加、插入、删除、反转
- 不需要像 `String` 那样每次都生成一个新对象

## 4. 三者的核心区别

### String

- 不可变
- 适合内容基本不改的场景

### StringBuffer

- 可变
- 线程安全
- 效率一般低于 `StringBuilder`

### StringBuilder

- 可变
- 非线程安全
- 单线程环境下效率通常更高

一句话记忆：

- 少量操作用 `String`
- 单线程频繁拼接用 `StringBuilder`
- 多线程场景再考虑 `StringBuffer`

## 5. 常见创建方式

### 5.1 创建空对象

```java
StringBuffer sb1 = new StringBuffer();
StringBuilder sb2 = new StringBuilder();
```

### 5.2 用已有字符串初始化

```java
StringBuffer sb1 = new StringBuffer("abc");
StringBuilder sb2 = new StringBuilder("abc");
```

## 6. 常用方法

## 6.1 `append()`

追加内容。

```java
StringBuilder sb = new StringBuilder();
sb.append("hello");
sb.append(" ");
sb.append("world");
System.out.println(sb);
```

这是最常用的方法。

## 6.2 `insert()`

在指定位置插入内容。

```java
StringBuilder sb = new StringBuilder("abc");
sb.insert(1, "hello");
System.out.println(sb);
```

## 6.3 `delete()`

删除一段区间内容。

```java
StringBuilder sb = new StringBuilder("abcdef");
sb.delete(2, 4);
System.out.println(sb);
```

注意：

- 也是左闭右开

## 6.4 `replace()`

替换一段区间内容。

```java
StringBuilder sb = new StringBuilder("abcdef");
sb.replace(2, 4, "hello");
System.out.println(sb);
```

## 6.5 `reverse()`

反转字符串内容。

```java
StringBuilder sb = new StringBuilder("abcdef");
sb.reverse();
System.out.println(sb);
```

## 6.6 `toString()`

把 `StringBuffer` 或 `StringBuilder` 转成 `String`。

```java
StringBuilder sb = new StringBuilder("hello");
String str = sb.toString();
```

## 7. 长度与容量

这是一个基础但容易被忽略的点。

### `length()`

表示当前已有字符的长度。

### `capacity()`

表示当前底层可容纳的容量。

例如：

```java
StringBuilder sb = new StringBuilder();
System.out.println(sb.length());
System.out.println(sb.capacity());
```

复习时先知道：

- `length()` 看当前内容长度
- `capacity()` 看底层空间大小

## 8. 为什么它们效率更高

因为它们是可变的。

例如不断 `append()` 时：

- 大多数情况下是在原有容器上修改
- 不会像 `String` 那样每次都创建全新的字符串对象

所以在循环拼接、批量处理文本时更合适。

## 9. 常见使用场景

### 场景 1：循环拼接

```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 100; i++) {
    sb.append(i);
}
System.out.println(sb.toString());
```

### 场景 2：构造一段复杂文本

例如拼 SQL、日志、提示信息。

### 场景 3：反转字符串

```java
StringBuilder sb = new StringBuilder("abcdef");
System.out.println(sb.reverse());
```

## 10. 当前阶段最该掌握的结论

你现在至少要记住这几件事：

1. `String` 不可变
2. `StringBuffer` 和 `StringBuilder` 可变
3. 频繁修改字符串时优先考虑 `StringBuilder`
4. `StringBuffer` 是线程安全的
5. 常用方法是 `append()`、`insert()`、`delete()`、`replace()`、`reverse()`、`toString()`

## 11. 一句话总结

`StringBuffer` 和 `StringBuilder` 本质上就是为了解决 `String` 频繁拼接效率低的问题。
