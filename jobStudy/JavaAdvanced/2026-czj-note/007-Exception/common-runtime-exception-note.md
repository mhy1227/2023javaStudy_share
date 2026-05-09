# 常见运行时异常

## 1. 为什么要单独整理运行时异常

异常这一章里，最常被追问举例的，往往不是：

- `IOException`
- `SQLException`

而是：

- 常见运行时异常有哪些

因为这类异常和日常写代码、刷题、做业务开发的关系最直接。

所以这一篇重点不是讲体系，而是讲：

1. 常见类型
2. 典型场景
3. 面试时怎么答

## 2. RuntimeException 是什么

`RuntimeException` 属于：

- `Exception`

同时通常也被理解成：

- unchecked exception

它的特点可以先粗记为：

- 编译期通常不强制你显式处理
- 更偏代码逻辑、边界、参数、类型问题

## 3. 最常见的几类运行时异常

### 3.1 NullPointerException

最典型例子：

```java
String name = null;
System.out.println(name.length());
```

最常见业务场景：

1. 查询结果为 `null`
2. 参数判空不严
3. 对象嵌套属性直接连着取

面试答法：

`NullPointerException` 是最常见的运行时异常之一，通常反映对象可能为空但代码里没有做判空保护。

### 3.2 IndexOutOfBoundsException

最典型例子：

```java
List<Integer> list = new ArrayList<>();
list.add(1);
System.out.println(list.get(1));
```

常见延伸：

1. `ArrayIndexOutOfBoundsException`
2. `StringIndexOutOfBoundsException`

最常见业务场景：

1. 循环边界写错
2. 数组长度判断不严
3. 字符串截取位置有问题

### 3.3 ArithmeticException

最典型例子：

```java
int a = 10 / 0;
```

业务里常见场景：

1. 算比例
2. 算平均值
3. 算转化率时分母没校验

### 3.4 NumberFormatException

最典型例子：

```java
int age = Integer.parseInt("18岁");
```

业务里常见场景：

1. 前端参数不规范
2. Excel 导入脏数据
3. 数据库存的值不能直接转数字

### 3.5 ClassCastException

最典型例子：

```java
Object obj = "hello";
Integer num = (Integer) obj;
```

业务里常见场景：

1. 强转前没判断真实类型
2. 老代码大量用 `Object`
3. 泛型约束不严

### 3.6 IllegalArgumentException

这个异常在业务代码里特别常见。

最典型例子：

```java
public void setAge(int age) {
    if (age < 0) {
        throw new IllegalArgumentException("age < 0");
    }
}
```

适合场景：

1. 参数非法
2. 参数格式不对
3. 业务前置条件不满足

### 3.7 IllegalStateException

这个异常也很常见，但很多人第一轮复习容易漏。

最典型感觉是：

- 参数本身没问题
- 但当前对象状态不对

例如：

```java
if (orderStatus != PAID) {
    throw new IllegalStateException("order status invalid");
}
```

适合场景：

1. 订单状态不合法
2. 资源状态不允许当前操作
3. 对象还没初始化完成

## 4. 面试里最常让你举哪几种

通常最常让你顺口举出来的是：

1. `NullPointerException`
2. `IndexOutOfBoundsException`
3. `ClassCastException`
4. `ArithmeticException`
5. `NumberFormatException`

如果你还能顺手补两个业务里常用的：

6. `IllegalArgumentException`
7. `IllegalStateException`

会更完整一点。

## 5. 怎么把这些异常分成两组来记

### 第一组：刷题和基础代码里最常见

1. `NullPointerException`
2. `IndexOutOfBoundsException`
3. `ArithmeticException`
4. `NumberFormatException`
5. `ClassCastException`

### 第二组：业务代码里很常主动抛

1. `IllegalArgumentException`
2. `IllegalStateException`

这样记会更实用。

## 6. 面试里怎么答更稳

可以这样答：

常见运行时异常我一般会分成两组记。第一组是最常见的基础异常，比如空指针、越界、类型转换失败、数字转换失败、除零异常；第二组是业务里经常主动抛的异常，比如 `IllegalArgumentException` 和 `IllegalStateException`。前一组更偏代码边界问题，后一组更偏业务规则和对象状态校验。

## 7. 当前阶段最容易混的点

1. `RuntimeException` 属于 `Exception`
2. `IllegalArgumentException` 和 `IllegalStateException` 不一样
3. 越界异常其实有多个具体子类
4. 很多运行时异常不是“等它抛”，而是要提前校验避免

## 8. 当前阶段最该记住的结论

1. 最常见运行时异常一定要能顺口举例
2. 空指针、越界、类型转换、数字转换失败非常高频
3. `IllegalArgumentException` 和 `IllegalStateException` 在业务里很好用
4. 运行时异常更偏逻辑、边界和状态问题

## 9. 一句话总结

常见运行时异常这块，重点不是把类名背得很多，而是知道哪些最常见、为什么会发生、业务里怎么预防。
