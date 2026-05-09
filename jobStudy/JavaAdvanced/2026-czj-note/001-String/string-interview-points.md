# String 高频面试点

## 1. String 为什么不可变

这是最常见的问题之一。

核心回答：

- `String` 底层用于存储字符内容的结构不会被随意修改
- 一旦对象创建完成，内容就固定了
- 所有“修改”操作，本质上都是创建新字符串

常见意义：

- 安全性更高
- 可以安全复用字符串常量池
- 适合作为 `HashMap` 的 key

## 2. `==` 和 `equals()` 的区别

### `==`

比较的是：

- 两个引用变量保存的地址是否相同

### `equals()`

比较的是：

- 两个字符串内容是否相同

例如：

```java
String s1 = "abc";
String s2 = "abc";
String s3 = new String("abc");

System.out.println(s1 == s2);
System.out.println(s1 == s3);
System.out.println(s1.equals(s3));
```

复习时直接记：

- 比内容，优先 `equals()`
- `==` 只适合判断是不是同一个对象

## 3. 字符串常量池是什么

简单理解：

- 直接写的字符串字面量会优先进入常量池
- 相同内容的字面量可能会复用

例如：

```java
String s1 = "hello";
String s2 = "hello";
```

这两个变量很可能指向常量池中的同一个字符串对象。

但：

```java
String s3 = new String("hello");
```

这里会额外创建对象。

## 4. `new String("abc")` 创建了几个对象

这是高频经典题。

面试里通常这样回答更稳：

- 如果常量池里还没有 `"abc"`，则可能涉及常量池对象和堆对象
- `new String("abc")` 至少会在堆里创建一个新的 `String` 对象

初学阶段不必死抠不同 JDK 版本的细节，先把核心逻辑说清楚：

- 字面量和 `new` 的行为不同
- `new` 一定会创建新的堆对象

## 5. 为什么 String 适合做 HashMap 的 key

因为：

- 不可变
- `hashCode()` 结果稳定

如果 key 可变，放进 `HashMap` 后再修改内容，会导致哈希定位出问题。

## 6. String、StringBuffer、StringBuilder 的区别

### String

- 不可变
- 适合读多改少

### StringBuffer

- 可变
- 线程安全
- 效率一般低于 `StringBuilder`

### StringBuilder

- 可变
- 非线程安全
- 单线程下拼接效率更高

一句话记忆：

- 少量字符串操作用 `String`
- 单线程大量拼接用 `StringBuilder`
- 多线程环境再考虑 `StringBuffer`

## 7. 为什么字符串拼接不要总用 `+`

例如在循环里：

```java
String s = "";
for (int i = 0; i < 1000; i++) {
    s += i;
}
```

问题在于：

- 每次拼接都可能产生新字符串对象
- 性能开销大

更合适的是：

```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);
}
String result = sb.toString();
```

## 8. `intern()` 是什么

可以简单理解为：

- 尝试返回字符串常量池中的引用

这个点属于稍进阶内容，当前阶段先知道它和常量池相关即可，不需要一上来深挖。

## 9. String 常见易错点

### 9.1 `isEmpty()` 不是判 `null`

```java
String s = null;
// s.isEmpty();  // 会空指针
```

### 9.2 `trim()` 只去首尾空格

它不会删掉中间空格。

### 9.3 `substring()` 左闭右开

```java
str.substring(2, 5)
```

表示取：

- 2
- 3
- 4

不包含 5。

### 9.4 单引号是 `char`

```java
'a'
```

不是：

```java
'abc'
```

后者会直接报错。

## 10. 复习时最值得掌握的回答模板

### 问：String 为什么不可变

答：

- `String` 内容创建后不能直接改
- 所有修改操作都会返回新字符串
- 这样能保证安全性、常量池复用和哈希稳定性

### 问：`==` 和 `equals()` 区别

答：

- `==` 比较地址
- `equals()` 比较内容

### 问：String 和 StringBuilder 的区别

答：

- `String` 不可变
- `StringBuilder` 可变，适合频繁拼接

## 11. 当前阶段怎么用这份笔记

建议你先把下面几个点说顺：

1. String 不可变
2. `==` 和 `equals()`
3. 常量池的基本理解
4. `StringBuilder` 的使用场景
5. 常见方法和易错点

如果这 5 个点能自己说顺，String 这一块的基础就算搭起来了。
