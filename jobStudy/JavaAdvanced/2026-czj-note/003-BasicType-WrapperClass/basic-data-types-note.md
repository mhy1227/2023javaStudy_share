# 基本数据类型基础笔记

## 1. 什么是基本数据类型

Java 中的基本数据类型一共有 8 个：

- `byte`
- `short`
- `int`
- `long`
- `float`
- `double`
- `char`
- `boolean`

它们的特点是：

- 表示的是最基础的数据值
- 不是对象
- 不是类

## 2. 基本数据类型的分类

### 2.1 整数类型

- `byte`
- `short`
- `int`
- `long`

### 2.2 浮点类型

- `float`
- `double`

### 2.3 字符类型

- `char`

### 2.4 布尔类型

- `boolean`

## 3. 最常用的是哪些

日常最常见的是：

- `int`
- `double`
- `char`
- `boolean`

其中：

- 整数默认更常用 `int`
- 小数默认更常用 `double`

## 4. 基本示例

```java
int age = 18;
double price = 12.5;
char gender = '男';
boolean flag = true;
```

## 5. `long` 和 `float` 的字面量注意点

### `long`

```java
long num = 123L;
```

建议加 `L`。

### `float`

```java
float score = 12.5F;
```

建议加 `F`。

因为默认小数字面量是 `double`。

## 6. `char` 的特点

`char` 用来表示单个字符。

例如：

```java
char c1 = 'A';
char c2 = '中';
```

注意：

- `char` 用单引号
- 只能放一个字符

错误示例：

```java
char c = 'ab';
```

## 7. `boolean` 的特点

`boolean` 只有两个值：

- `true`
- `false`

它不能像某些语言那样直接拿 `0` 和 `1` 代替。

错误示例：

```java
boolean flag = 1;
```

## 8. 为什么基本类型重要

因为它们是后面很多概念的基础：

- 运算
- 方法传参
- 自动装箱拆箱
- 包装类
- `final` 修饰变量

## 9. 当前阶段最该掌握的结论

1. Java 一共有 8 个基本数据类型
2. 基本数据类型不是对象
3. `char` 用单引号
4. `boolean` 只有 `true` 和 `false`
5. `long` 常配 `L`，`float` 常配 `F`

## 10. 一句话总结

基本数据类型是 Java 最基础的数据表示方式，后面的包装类、引用类型、对象概念都要建立在它之上。
