# 牛客高频面试题：题目版

## 1. String 相关

1. `String`、`StringBuilder`、`StringBuffer` 的区别是什么？
2. 为什么 `String` 是不可变的？
3. 为什么 `String` 适合作为 `HashMap` 的 key？
4. `String s1 = "123"` 和 `String s2 = new String("123")` 有什么区别？
5. `==` 和 `equals()` 比较字符串时分别在比什么？
6. 什么是字符串常量池？
7. `intern()` 是什么？返回的是什么？

## 2. 基本类型与包装类

1. Java 有哪些基本数据类型？
2. 基本类型和引用类型的区别是什么？
3. 为什么 Java 要引入包装类？
4. `int` 和 `Integer` 的区别是什么？
5. 自动装箱和自动拆箱是什么？
6. 包装类的默认值是什么？
7. `parseXxx()`、`valueOf()`、`xxxValue()` 有什么区别？
8. 为什么 `Integer a = 100; Integer b = 100; a == b` 可能是 `true`？
9. 为什么 `Integer a = 200; Integer b = 200; a == b` 可能是 `false`？

## 3. 类型转换

1. 什么是自动类型提升？
2. 什么场景下需要强制类型转换？
3. 强制类型转换可能带来什么问题？
4. `byte b = (byte)128;` 为什么结果异常？
5. `char` 在运算时要注意什么？

## 4. 业务字段类型选择

1. 为什么手机号通常定义成 `String`，而不是 `long`？
2. 为什么身份证号、学号、订单号通常也更适合 `String`？
3. 什么字段适合用数值类型，什么字段适合用 `String`？

## 5. final 与对象

1. `final` 修饰基本类型和引用类型有什么区别？
2. `final` 为什么不等于对象不可变？
3. `String` 不可变和 `final` 有什么关系？
