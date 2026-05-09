# valueOf、parseXxx、xxxValue 的区别

## 1. 为什么这个点容易混

学包装类时，最容易混的就是这三类方法：

- `valueOf()`
- `parseXxx()`
- `xxxValue()`

它们名字很像，但转换方向不一样。

## 2. 一句话先记住

- `parseXxx()`：`String -> 基本类型`
- `valueOf()`：`String/基本类型 -> 包装类对象`
- `xxxValue()`：`包装类对象 -> 基本类型`

## 3. `parseXxx()` 是什么

以 `Integer` 为例：

```java
int num = Integer.parseInt("123");
```

这里的作用是：

- 把字符串 `"123"` 转成基本类型 `int`

其他常见写法：

```java
double d = Double.parseDouble("12.5");
boolean flag = Boolean.parseBoolean("true");
```

## 4. `valueOf()` 是什么

### 4.1 字符串转包装类对象

```java
Integer num = Integer.valueOf("123");
Double d = Double.valueOf("12.5");
```

这里得到的是：

- 包装类对象

不是基本类型。

### 4.2 基本类型转包装类对象

```java
Integer num = Integer.valueOf(123);
Double d = Double.valueOf(12.5);
```

这本质上就是手动装箱。

## 5. `xxxValue()` 是什么

这是包装类对象转回基本类型的方法。

例如：

```java
Integer num = 123;
int x = num.intValue();
```

其他类似方法：

- `doubleValue()`
- `longValue()`
- `byteValue()`
- `charValue()`

## 6. 三者对比示例

```java
String s = "123";

int a = Integer.parseInt(s);   // String -> int
Integer b = Integer.valueOf(s); // String -> Integer
int c = b.intValue();           // Integer -> int
```

## 7. 最容易混的地方

### 7.1 `parseInt()` 返回的不是 `Integer`

很多人会误以为：

```java
Integer.parseInt("123")
```

返回的是 `Integer`。

其实返回的是：

- `int`

### 7.2 `valueOf()` 返回的是对象

```java
Integer.valueOf("123")
```

返回的是：

- `Integer`

### 7.3 `xxxValue()` 的调用者必须是包装类对象

例如：

```java
Integer num = 10;
int x = num.intValue();
```

而不是直接对基本类型调用。

## 8. 什么时候用哪一个

### 用 `parseXxx()`

当你要的是：

- 基本类型值

例如：

```java
int age = Integer.parseInt("18");
```

### 用 `valueOf()`

当你要的是：

- 包装类对象

例如：

```java
Integer age = Integer.valueOf("18");
```

### 用 `xxxValue()`

当你已经有一个包装类对象，想拿到基本类型值时。

## 9. 当前阶段最该掌握的结论

1. `parseXxx()` 返回基本类型
2. `valueOf()` 返回包装类对象
3. `xxxValue()` 把包装类对象转回基本类型
4. 三者本质上是不同方向的转换

## 10. 一句话总结

记方向比记名字更重要：`parseXxx` 往基本类型走，`valueOf` 往包装类走，`xxxValue` 从包装类再拆回基本类型。
