# final、引用、包装类与 String 不可变性

## 1. 为什么这个点值得单独讲

很多人在学 Java 基础时，会把下面几个概念混在一起：

- `final`
- 基本数据类型
- 引用数据类型
- 包装类
- `String` 不可变

最常见的误区是：

- 以为 `final` 修饰以后，对象就不可变了

这其实是不准确的。

## 2. 先分清两类数据

Java 里的数据可以先简单分成两大类：

### 2.1 基本数据类型

常见的有：

- `byte`
- `short`
- `int`
- `long`
- `float`
- `double`
- `char`
- `boolean`

这些类型本身表示的是值。

例如：

```java
int a = 10;
```

这里 `a` 保存的是数值 `10`。

### 2.2 引用数据类型

常见的有：

- 类
- 接口
- 数组
- `String`

例如：

```java
String s = "hello";
```

这里 `s` 不是直接装着整个字符串内容，而是一个引用变量，指向某个对象。

## 3. 什么是包装类

基本数据类型对应的包装类如下：

- `byte` -> `Byte`
- `short` -> `Short`
- `int` -> `Integer`
- `long` -> `Long`
- `float` -> `Float`
- `double` -> `Double`
- `char` -> `Character`
- `boolean` -> `Boolean`

包装类本质上是：

- 把基本数据类型包装成对象

例如：

```java
Integer num = 10;
Double price = 12.5;
Character ch = 'A';
```

这样做的意义是：

- 可以把原本只是“值”的内容，当作对象来使用
- 方便和集合、泛型、方法参数等场景配合

## 4. `final` 到底修饰的是什么

`final` 的核心作用是：

- 让某个变量不能再次赋值

注意，是“变量不能再次赋值”，不是直接等于“对象不可变”。

## 5. `final` 修饰基本类型

例如：

```java
final int a = 10;
// a = 20; // 报错
```

这里很好理解：

- `a` 保存的是一个值
- `final` 让这个值不能再改成别的值

所以在基本类型场景下，`final` 看起来就像“值不能变”。

## 6. `final` 修饰引用类型

例如：

```java
final StringBuilder sb = new StringBuilder("abc");
```

这里 `final` 限制的是：

- `sb` 这个引用变量不能再指向别的对象

也就是说下面这种写法不行：

```java
// sb = new StringBuilder("xyz"); // 报错
```

但是下面这种写法是可以的：

```java
sb.append("def");
System.out.println(sb);
```

因为：

- `sb` 没有重新指向别的对象
- 改的是对象内部内容

## 7. 为什么 `final` 不等于对象不可变

看这个例子：

```java
final StringBuilder sb = new StringBuilder("abc");
sb.append("def");
System.out.println(sb);
```

输出：

```text
abcdef
```

这说明：

- `final` 没有让 `StringBuilder` 对象不可变
- 它只是让 `sb` 这个引用不许再指向别处

所以一个很重要的结论是：

- `final` 修饰引用，只保证引用不变
- 不保证对象内部状态不变

## 8. 什么才叫不可变对象

不可变对象的意思是：

- 对象一旦创建完成，内部状态就不能再修改

这是一种类设计上的特性，不是只靠 `final` 三个字母就自动成立。

## 9. String 为什么不可变

`String` 不可变，不是因为你写代码时给它加了 `final`。

更准确地说：

- `String` 这个类本身就是按照不可变对象的思路设计的
- 它的内容创建后不能被直接改动
- 所有“修改字符串”的操作，本质上都会返回一个新字符串

例如：

```java
String s = "abc";
String s2 = s.replace("a", "m");

System.out.println(s);
System.out.println(s2);
```

输出：

```text
abc
mbc
```

这说明：

- 原来的 `"abc"` 没有被改掉
- 只是产生了一个新的 `"mbc"`

## 10. `String` 是什么对象

`String` 不是基本数据类型。

它是：

- `java.lang.String` 这个类的对象

所以：

```java
String s = "hello";
```

这里的 `s` 是一个引用变量，它指向一个 `String` 对象。

当前阶段你可以直接记：

- `String` 是引用类型
- `String` 是对象
- `String` 不是基本类型

## 11. 包装类和 String 有什么共同点

它们有两个重要共同点：

1. 都是引用类型
2. 都是对象

例如：

```java
Integer a = 10;
String b = "hello";
```

这里：

- `a` 是对象引用
- `b` 也是对象引用

所以它们和 `int`、`double` 这种基本类型不同。

## 12. 包装类和 String 的一个重要区别

虽然包装类和 `String` 都是对象，但你当前最需要先记住的是：

- `String` 明确是不可变对象
- 常见包装类也通常按值语义使用，但你当前复习重点还是放在 `String` 的不可变性上

当前阶段先不要把这块扩展得太重，只要知道：

- `String` 不可变是特别重要的基础点

## 13. 一组最典型的对比例子

### 例 1：基本类型 + final

```java
final int x = 10;
// x = 20; // 不允许
```

### 例 2：引用类型 + final

```java
final StringBuilder sb = new StringBuilder("abc");
sb.append("def"); // 允许
// sb = new StringBuilder("xyz"); // 不允许
```

### 例 3：String 不可变

```java
String s = "abc";
s.replace("a", "m");
System.out.println(s); // 还是 abc
```

### 例 4：正确接收新字符串

```java
String s = "abc";
s = s.replace("a", "m");
System.out.println(s); // mbc
```

## 14. 最容易混淆的地方

你复习时要特别防止混成一句话：

- “`final` 修饰以后对象就不可变”

这句话不对。

更准确的表达应该是：

- `final` 修饰基本类型时，值不能再改
- `final` 修饰引用类型时，引用不能再指向别的对象
- 对象本身是否可变，要看这个类怎么设计
- `String` 不可变，是类设计决定的

## 15. 当前阶段最该记住的结论

你至少要记住下面 5 句话：

1. 基本类型保存的是值
2. 引用类型保存的是对象引用
3. 包装类是把基本类型包装成对象
4. `final` 不等于对象不可变
5. `String` 是对象，而且是不可变对象

## 16. 一句话总结

`final` 约束的是变量绑定，`String` 的不可变来自类设计，这两个概念相关，但绝不是一回事。
