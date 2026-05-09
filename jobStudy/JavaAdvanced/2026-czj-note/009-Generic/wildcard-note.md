# 通配符基础笔记

## 1. 为什么通配符特别容易卡住

前面的泛型类、泛型方法、泛型接口，更多还是在说：

- 怎么声明泛型

但真正开始使用泛型时，很快就会遇到：

- `?`
- `? extends`
- `? super`

这个时候很多人会觉得：

- 尖括号突然变复杂了

所以通配符必须单独讲。

## 2. 什么是通配符

通配符可以先理解成：

- 泛型里表示“某种未知类型”的写法

最基础的就是：

- `?`

例如：

```java
List<?> list
```

这里可以先理解成：

- 这是一个列表
- 但列表里的具体类型现在不确定

## 3. 为什么需要通配符

因为有时候你只关心：

- 这是一个泛型结构

但你并不想把具体类型写死。

也就是说，通配符的核心价值可以先记成：

- 在“类型不确定”时，给泛型提供更灵活的表达方式

## 4. 最基础的 `?`

例如：

```java
public void printList(List<?> list) {
    for (Object obj : list) {
        System.out.println(obj);
    }
}
```

这里更自然的理解是：

- 我只想遍历、打印
- 我不关心列表里具体是 `String`、`Integer` 还是别的类型

所以这里用：

- `List<?>`

就很自然。

## 5. `?` 为什么通常不适合随便 add

这个点很高频。

例如：

```java
List<?> list = new ArrayList<String>();
```

这里你不能很随便地：

```java
list.add("hello");
```

因为：

- 你虽然知道它是某种列表
- 但编译器并不知道它里面到底应该放什么具体类型

所以更稳的直觉可以先记成：

- `?` 更适合读，不适合随便写

## 6. `? extends` 是什么

`? extends Xxx` 可以先理解成：

- 某种 `Xxx` 或它的子类型

例如：

```java
List<? extends Number> list
```

这里可以先理解成：

- 这是一个列表
- 里面装的是 `Number` 体系下的某种类型
- 可能是 `Integer`
- 也可能是 `Double`

## 7. `? extends` 为什么更偏读

例如：

```java
List<? extends Number> list
```

这里你通常可以更自然地：

- 把元素按 `Number` 读出来

但不适合随便往里 add 一个 `Integer` 或 `Double`。

因为编译器知道的是：

- 它是某种 `Number` 子类型

但不知道到底是哪一种。

所以更稳的直觉可以先记成：

- `? extends` 更适合读

## 8. `? super` 是什么

`? super Xxx` 可以先理解成：

- 某种 `Xxx` 或它的父类型

例如：

```java
List<? super Integer> list
```

这里可以先理解成：

- 这是一个能接受 `Integer` 的更宽泛容器

它可能实际是：

- `List<Integer>`
- `List<Number>`
- `List<Object>`

## 9. `? super` 为什么更偏写

例如：

```java
List<? super Integer> list = new ArrayList<Number>();
list.add(100);
```

这里更自然的理解是：

- 既然它至少能容纳 `Integer`
- 那往里写 `Integer` 会比较安全

所以更稳的直觉可以先记成：

- `? super` 更适合写

## 10. 一个最常见的记忆口诀

可以先粗记成：

- `? extends` 偏读
- `? super` 偏写

这个口诀不是为了死背，而是为了先建立方向感。

## 11. 一个更直观的对比例子

```java
public void readNumbers(List<? extends Number> list) {
    Number n = list.get(0);
}

public void writeIntegers(List<? super Integer> list) {
    list.add(100);
}
```

这里的直觉就是：

- 上面那个方法更像“我要读”
- 下面那个方法更像“我要写”

## 12. 通配符这块面试里容易问什么

常见问题有：

1. 什么是通配符
2. `?`、`? extends`、`? super` 的区别
3. 为什么 `List<?>` 不能随便 add
4. 为什么说 `extends` 偏读、`super` 偏写

## 13. 当前阶段最容易混的点

1. `?` 不是具体类型
2. `? extends` 不是“只能放父类”
3. `? super` 不是“只能放子类”
4. 通配符的关键是类型范围和读写边界
5. 口诀只是帮助理解，不是替代思考

## 14. 当前阶段最该记住的结论

1. 通配符表示某种未知类型
2. `?` 表示未知但不具体
3. `? extends` 更偏读
4. `? super` 更偏写
5. 通配符的核心是在使用泛型时提供更灵活的类型范围表达

## 15. 一句话总结

通配符最核心的意义，就是在“类型不完全确定”时，给泛型提供更灵活的读写边界和范围控制。
