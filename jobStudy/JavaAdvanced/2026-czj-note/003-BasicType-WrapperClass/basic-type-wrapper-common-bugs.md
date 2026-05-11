# 基本类型与包装类常见易错点

## 1. 忘记默认整数是 `int`

例如：

```java
long num = 1234567890123;
```

这种写法可能有问题，通常应写成：

```java
long num = 1234567890123L;
```

## 2. 忘记默认小数是 `double`

例如：

```java
float score = 12.5;
```

应改成：

```java
float score = 12.5F;
```

## 3. 把包装类和基本类型完全当成一样

例如：

```java
Integer a = 10;
int b = 10;
```

它们看起来像，但本质不同：

- `Integer` 是对象
- `int` 是基本类型

## 4. 忘记包装类默认值是 `null`

成员变量里：

```java
int a;       // 默认 0
Integer b;   // 默认 null
```

这个区别很重要。

## 5. 自动拆箱时忽略空指针

例如：

```java
Integer num = null;
int x = num;
```

这里会报：

- `NullPointerException`

## 6. `parseXxx()` 和 `valueOf()` 混淆

错误理解常见于：

- 以为 `parseInt()` 返回 `Integer`

其实：

- `parseInt()` 返回 `int`
- `valueOf()` 返回 `Integer`

## 7. 强转后以为结果一定“只是截断”

有些强转不仅会截断，还可能溢出。

例如：

```java
byte b = (byte) 128;
```

这不是正常保留原值。

## 8. 认为手机号应该用 long

这是非常常见的业务误区。

手机号应优先用：

- `String`

因为它更像标识，不是运算值。

## 9. 把 `char` 当字符串用

例如：

```java
char c = 'A';
```

这是单个字符。

不是：

```java
String s = "A";
```

## 10. 当前阶段最该避免的错误

1. `long` 不加 `L`
2. `float` 不加 `F`
3. 忘记包装类是对象
4. 忘记包装类默认值可能是 `null`
5. 自动拆箱时没做空判断
6. 误把手机号、身份证号这类字段定义成数值类型

## 11. 一句话总结

这一章最容易出错的地方，不是概念不会，而是“看起来差不多”的类型其实行为不一样。
