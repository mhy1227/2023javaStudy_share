# String 类的继承关系与结构

## 1. String 继承谁

`String` 直接继承的是：

- `Object`

可以简单理解成：

```java
String -> Object
```

也就是说，`String` 没有继承什么复杂的中间父类，它的父类就是 Java 中所有类的根类：

- `java.lang.Object`

## 2. String 的类定义可以怎么理解

通常可以这样理解：

```java
public final class String
    extends Object
    implements Serializable, Comparable<String>, CharSequence
```

当前阶段不用死记源码细节，但这几个部分很值得记住。

## 3. 为什么说 String 是 `final` 类

`String` 前面有：

- `final`

这表示：

- `String` 不能被继承

例如你不能写：

```java
class MyString extends String {
}
```

这是不允许的。

## 4. String 既然继承了 Object，有什么意义

因为 `Object` 是所有类的父类，所以 `String` 天然也具备 `Object` 的基础能力。

例如你会接触到这些方法：

- `toString()`
- `equals()`
- `hashCode()`

注意：

- 这些方法来自 `Object`
- 但 `String` 对其中一些方法做了重写

所以 `String` 才能实现：

- 按内容比较
- 根据内容生成哈希值

这也是它适合做 `HashMap` key 的重要原因之一。

## 5. String 实现了哪些常见接口

当前阶段重点记 3 个就够了：

### 5.1 `Serializable`

表示：

- `String` 对象可以被序列化

### 5.2 `Comparable<String>`

表示：

- `String` 对象之间可以比较大小

这也是为什么我们能写：

```java
"abc".compareTo("abd");
```

### 5.3 `CharSequence`

表示：

- `String` 本质上是一种字符序列

像下面这些类，也和字符序列这个概念有关：

- `String`
- `StringBuilder`
- `StringBuffer`

## 6. String 是对象吗

是的，`String` 是对象。

它不是基本数据类型。

例如：

```java
String s = "hello";
```

这里：

- `s` 是引用变量
- 它指向的是一个 `String` 对象

所以 `String` 的定位一定要记准：

- 它是引用类型
- 它是类
- 它的实例是对象

## 7. String 为什么设计成 final

当前阶段可以先记住一个基础理解：

- `String` 经常被广泛使用
- 它又和常量池、哈希、不可变性这些机制强相关
- 设计成 `final`，更有利于保证行为稳定

你现在不需要把这块展开得太底层，只要知道：

- `String` 不能被继承
- 这是它设计上的一部分

## 8. 当前阶段最该记住的结论

你至少要记住下面这些：

1. `String` 的父类是 `Object`
2. `String` 是 `final` 类
3. `String` 不能被继承
4. `String` 实现了 `Serializable`、`Comparable<String>`、`CharSequence`
5. `String` 是对象，不是基本数据类型

## 9. 一句话总结

`String` 本质上是一个继承自 `Object` 的 `final` 类对象，同时实现了字符序列、比较和序列化相关接口。
