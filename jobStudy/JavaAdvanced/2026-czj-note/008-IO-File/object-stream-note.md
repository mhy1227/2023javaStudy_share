# 对象流基础笔记

## 1. 为什么还要有对象流

前面的流大多是在处理：

- 字节
- 字符
- 文本

但实际开发里还有一种很常见的需求：

- 直接把对象写出去
- 再把对象读回来

例如：

- 把对象保存到文件
- 在网络里传输对象

这时候就会接触到：

- 对象流

## 2. 什么是对象流

对象流可以先理解成：

- 能把对象写出去、也能把对象读回来的流

最常见的两个类是：

1. `ObjectOutputStream`
2. `ObjectInputStream`

## 3. 对象流和什么概念强相关

对象流后面最重要的一个词就是：

- 序列化

可以先粗记：

### 序列化

- 把对象转换成可以保存或传输的形式

### 反序列化

- 再把这种形式恢复成对象

所以对象流通常总会和：

- 序列化
- 反序列化

放在一起讲。

## 4. ObjectOutputStream 是什么

`ObjectOutputStream` 可以先理解成：

- 把对象写出去

示例：

```java
ObjectOutputStream oos =
        new ObjectOutputStream(new FileOutputStream("D:/user.dat"));
oos.writeObject("hello");
oos.close();
```

这个例子里：

- `"hello"` 本质上是对象
- 通过对象流被写到了文件里

## 5. ObjectInputStream 是什么

`ObjectInputStream` 可以先理解成：

- 把之前写出去的对象再读回来

示例：

```java
ObjectInputStream ois =
        new ObjectInputStream(new FileInputStream("D:/user.dat"));
Object obj = ois.readObject();
System.out.println(obj);
ois.close();
```

这里可以先理解成：

- 文件里存的是对象数据
- 现在把它再读回程序里

## 6. 自定义对象为什么不能随便写

这个点很重要。

如果你写的是普通字符串、包装类，很多时候问题不大。

但如果是自定义对象，一般会遇到一个前提：

- 这个类要支持序列化

最常见的做法就是：

- 实现 `Serializable`

例如：

```java
class User implements Serializable {
    private String name;
    private int age;
}
```

## 7. Serializable 是什么

可以先理解成：

- 一个标记接口

它本身不强调你去实现什么方法，而更像是在告诉 Java：

- 这个类的对象允许被序列化

所以这里先有一个印象就够了：

- 自定义对象想用对象流，通常要先实现 `Serializable`

## 8. 一个完整一点的例子

```java
import java.io.*;

class User implements Serializable {
    String name;
    int age;

    User(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

public class Test {
    public static void main(String[] args) throws Exception {
        ObjectOutputStream oos =
                new ObjectOutputStream(new FileOutputStream("D:/user.dat"));
        oos.writeObject(new User("Tom", 18));
        oos.close();

        ObjectInputStream ois =
                new ObjectInputStream(new FileInputStream("D:/user.dat"));
        User user = (User) ois.readObject();
        System.out.println(user.name);
        ois.close();
    }
}
```

这个例子把：

- 写对象
- 读对象

两步都串起来了。

## 9. 对象流这块面试里容易问什么

常见问题有：

1. 什么是序列化和反序列化
2. `ObjectOutputStream` 和 `ObjectInputStream` 是做什么的
3. 自定义对象为什么要实现 `Serializable`
4. 对象流和字节流是什么关系

## 10. 对象流和字节流是什么关系

这个点容易混。

可以先理解成：

- 对象流本质上还是建立在更底层的流之上

例如常见写法里会看到：

- `new ObjectOutputStream(new FileOutputStream(...))`
- `new ObjectInputStream(new FileInputStream(...))`

也就是说：

- 底层还是文件字节流
- 对象流是在上层加了“对象读写”的能力

## 11. 当前阶段最容易混的点

1. 对象流不是普通文本流
2. 对象流和序列化强相关
3. 自定义对象通常不能直接随便写，往往要实现 `Serializable`
4. `ObjectInputStream` 读回来的是对象，常要做强转

## 12. 当前阶段最该记住的结论

1. 对象流用于读写对象
2. `ObjectOutputStream` 负责写对象
3. `ObjectInputStream` 负责读对象
4. 对象流和序列化 / 反序列化强相关
5. 自定义对象通常要实现 `Serializable`

## 13. 一句话总结

对象流最核心的意义，就是把“读写字节 / 字符”升级成“直接读写对象”。
