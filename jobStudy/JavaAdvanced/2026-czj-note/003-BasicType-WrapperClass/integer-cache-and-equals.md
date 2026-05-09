# Integer 缓存与 equals

## 1. 为什么这个点容易出题

`Integer` 是包装类里最容易被拿来出题的一个。

因为它同时会牵涉：

- 包装类对象
- 自动装箱
- `==`
- `equals()`
- 缓存机制

## 2. 一个经典例子

```java
Integer a = 100;
Integer b = 100;
System.out.println(a == b);
```

很多情况下这里会输出：

- `true`

但如果改成：

```java
Integer a = 200;
Integer b = 200;
System.out.println(a == b);
```

结果又可能是：

- `false`

## 3. 为什么会这样

因为 `Integer` 有缓存机制。

常见理解是：

- `Integer.valueOf()` 对 `[-128,127]` 范围内的整数会复用对象

所以：

```java
Integer a = 100;
Integer b = 100;
```

通常会指向同一个缓存对象。

而：

```java
Integer a = 200;
Integer b = 200;
```

通常不会复用同一个对象。

## 4. 为什么自动装箱也会受影响

例如：

```java
Integer a = 100;
```

这看起来像简单赋值，但底层可以理解为：

```java
Integer a = Integer.valueOf(100);
```

所以缓存机制会参与进来。

## 5. `==` 和 `equals()` 在 Integer 上的区别

### `==`

比较的是：

- 两个引用是不是同一个对象

### `equals()`

比较的是：

- 两个对象的值是否相同

例如：

```java
Integer a = 200;
Integer b = 200;

System.out.println(a == b);        // false
System.out.println(a.equals(b));   // true
```

## 6. `new Integer()` 的影响

如果写：

```java
Integer a = new Integer(100);
Integer b = new Integer(100);
System.out.println(a == b);
```

这里通常是：

- `false`

因为：

- `new` 会直接创建新的对象
- 不走缓存复用这条路

## 7. 当前阶段最稳的记法

复习时可以直接记：

1. `==` 比地址
2. `equals()` 比值
3. `Integer.valueOf()` 可能复用缓存对象
4. `new Integer()` 会创建新对象
5. `[-128,127]` 是常见缓存范围

## 8. 为什么面试喜欢问这个

因为它能同时考你：

- 包装类是不是对象
- 自动装箱发生了什么
- `==` 和 `equals()` 是否真的理解

## 9. 一句话总结

`Integer` 这类题的核心不是记答案，而是先记住：`==` 比引用，`equals()` 比值，缓存只会影响前者的结果。
