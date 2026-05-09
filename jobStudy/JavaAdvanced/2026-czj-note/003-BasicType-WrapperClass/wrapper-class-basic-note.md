# 包装类基础笔记

## 1. 什么是包装类

包装类就是：

- 把基本数据类型包装成对象对应的类

对应关系如下：

- `byte` -> `Byte`
- `short` -> `Short`
- `int` -> `Integer`
- `long` -> `Long`
- `float` -> `Float`
- `double` -> `Double`
- `char` -> `Character`
- `boolean` -> `Boolean`

## 2. 为什么需要包装类

因为 Java 中很多场景要求使用对象，而不是基本类型。

例如：

- 集合中不能直接放基本类型
- 泛型参数要求是引用类型
- 某些工具方法、API 更适合处理对象

## 3. 基本示例

```java
Integer age = 18;
Double price = 12.5;
Character ch = 'A';
Boolean flag = true;
```

这些都是对象，不是基本类型值本身。

## 4. 包装类和基本类型的关系

例如：

```java
int a = 10;
Integer b = 10;
```

区别是：

- `a` 是基本类型
- `b` 是对象引用

## 5. 常见包装类方法

当前阶段先知道两类最常见能力：

### 5.1 字符串转基本类型

```java
int num = Integer.parseInt("123");
double d = Double.parseDouble("12.5");
```

### 5.2 基本类型转字符串

```java
String str = String.valueOf(123);
```

## 6. 包装类的使用场景

最典型的是：

- 集合
- 泛型
- 工具类方法
- 自动装箱拆箱

## 7. 当前阶段最该掌握的结论

1. 包装类是基本类型对应的对象类型
2. `Integer` 对应 `int`
3. `Character` 对应 `char`
4. 包装类出现的核心原因是“有些场景只能用对象”

## 8. 一句话总结

包装类是连接“基本数据类型”和“对象世界”的桥梁。
