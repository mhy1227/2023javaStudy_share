# 自定义异常

## 1. 为什么还要讲自定义异常

前面已经有很多现成异常类了，例如：

- `IllegalArgumentException`
- `IllegalStateException`
- `RuntimeException`

那为什么还需要自定义异常？

因为实际业务里，经常会遇到这种情况：

- JDK 自带异常能抛
- 但语义不够清楚

也就是说，代码能跑，但表达不够准确。

## 2. 什么情况下会考虑自定义异常

最常见的场景是：

1. 业务语义很明确
2. 希望上层更容易区分错误类型
3. 希望日志和排查更直观

例如：

1. 库存不足
2. 订单状态非法
3. 用户未登录
4. 用户权限不足
5. 重复提交

这些都比单纯写：

```java
throw new RuntimeException("error");
```

更有表达力。

## 3. 自定义异常一般怎么选父类

当前阶段先记最实用的结论：

### 方式一：继承 RuntimeException

这是业务里很常见的方式。

适合：

- 业务异常
- 参数校验失败
- 规则校验失败

### 方式二：继承 Exception

适合：

- 你真的希望调用方显式处理

但在一般业务开发里，很多自定义异常更常见的是：

- 继承 `RuntimeException`

## 4. 一个最基础的自定义异常例子

```java
public class InventoryNotEnoughException extends RuntimeException {

    public InventoryNotEnoughException(String message) {
        super(message);
    }
}
```

使用时：

```java
if (stock < buyCount) {
    throw new InventoryNotEnoughException("库存不足");
}
```

这个写法的好处是：

- 一眼就知道是什么业务问题

## 5. 再看一个更贴近业务的例子

```java
public class OrderStatusException extends RuntimeException {

    public OrderStatusException(String message) {
        super(message);
    }
}
```

使用：

```java
if (order.getStatus() != OrderStatus.PAID) {
    throw new OrderStatusException("当前订单状态不允许发货");
}
```

这就比直接写：

```java
throw new RuntimeException("状态错误");
```

清晰得多。

## 6. 自定义异常的核心价值是什么

可以先总结成 3 点：

1. 语义清晰
2. 更方便分类处理
3. 更方便排查和日志定位

也就是说，它最大的价值不是“代码更高级”，而是：

- 错误表达更准确

## 7. 面试里怎么答更稳

可以这样答：

当 JDK 自带异常不能准确表达业务语义时，我会考虑自定义异常。比如库存不足、订单状态非法、用户未登录这类问题，用自定义异常会比直接抛 `RuntimeException` 更清晰。实际业务里很多自定义异常会继承 `RuntimeException`，这样既保留了运行时异常的使用习惯，也能把业务含义表达出来。

## 8. 自定义异常要注意什么

### 8.1 不要为了自定义而自定义

如果只是参数非法，其实很多时候直接用：

- `IllegalArgumentException`

就够了。

### 8.2 异常名要有业务语义

例如：

- `InventoryNotEnoughException`
- `OrderStatusException`

就比：

- `MyException`
- `BusinessException1`

更清楚。

### 8.3 异常信息不要太空

例如：

```java
throw new InventoryNotEnoughException("库存不足，商品ID=1001");
```

通常比：

```java
throw new InventoryNotEnoughException("error");
```

更有用。

但也要注意：

- 不要把敏感信息直接打出去

## 9. 业务异常和系统异常可以怎么粗分

这个也是常见追问。

可以先粗分成：

### 业务异常

- 规则不满足
- 状态不合法
- 用户操作不符合要求

例如：

- 库存不足
- 用户未登录
- 优惠券已失效

### 系统异常

- 数据库挂了
- 网络超时
- 文件读写失败

这类更偏底层资源和系统问题。

## 10. 当前阶段最容易混的点

1. 自定义异常不等于一定继承 `Exception`
2. 业务里很多自定义异常更常继承 `RuntimeException`
3. 自定义异常的重点是语义，不是炫技巧
4. 能直接用 JDK 异常时，不一定非要自定义

## 11. 当前阶段最该记住的结论

1. 自定义异常用于表达更明确的业务错误
2. 很多业务异常会继承 `RuntimeException`
3. 异常名和异常信息都要有业务语义
4. 不要为了自定义而自定义

## 12. 一句话总结

自定义异常的核心价值，不是“我写了一个新类”，而是“我把错误语义表达清楚了”。
