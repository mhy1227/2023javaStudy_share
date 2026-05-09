# 泛型牛客高频面试题示例回复

## 1. 这一份怎么用

这一份不是标准唯一答案，而是偏“面试能说顺”的示例回复。

使用建议：

- 先自己答
- 再对照这一份查漏补缺
- 最后把表述改成你自己的话

## 2. 为什么 Java 要引入泛型？

示例回复：

Java 引入泛型，核心是为了把类型检查尽量前移到编译期。这样可以提高类型安全，减少运行时的类型转换错误，也能减少很多强制类型转换代码。最典型的场景就是集合，如果没有泛型，`List` 里什么都能放，取出来时就容易出 `ClassCastException`。

简单例子：

```java
List<String> list = new ArrayList<>();
list.add("abc");
String s = list.get(0);
```

如果不用泛型，`get` 出来通常要自己强转。

## 3. 泛型为什么能提高类型安全？

示例回复：

因为很多类型错误会在编译期就被拦住，而不是拖到运行时。比如 `List<String>` 就明确规定这个集合里应该放 `String`，如果你尝试放 `Integer`，编译器会直接报错。

简单例子：

```java
List<String> list = new ArrayList<>();
// list.add(123); // 编译直接报错
```

## 4. 泛型类、泛型方法、泛型接口有什么区别？

示例回复：

区别主要在“泛型参数定义在什么层级”。

- 泛型类：泛型参数定义在类上，整个类都可以使用这个类型参数
- 泛型方法：泛型参数定义在方法上，只在当前方法里生效
- 泛型接口：泛型参数定义在接口上，由实现类决定具体类型

简单例子：

```java
class Box<T> {
    private T value;
}

class Util {
    public <T> T getFirst(T a, T b) {
        return a;
    }
}

interface Info<T> {
    T getData();
}
```

## 5. `T`、`E`、`K`、`V`、`R` 分别是什么意思？

示例回复：

它们本质上都只是类型参数名，没有强制规定，但有常见约定。

- `T`：Type，普通类型
- `E`：Element，集合元素
- `K`：Key，键
- `V`：Value，值
- `R`：Return，返回值类型

面试里可以顺带补一句：这些字母只是惯例，不是语法强制要求。

## 6. 什么是通配符 `?`？

示例回复：

`?` 表示未知类型。也就是说我知道这里是一个泛型类型，但我现在不关心它的具体类型参数到底是什么，或者暂时无法确定。

简单例子：

```java
public void printList(List<?> list) {
    for (Object obj : list) {
        System.out.println(obj);
    }
}
```

这个方法可以接收 `List<String>`、`List<Integer>` 等不同类型的列表。

## 7. `List<?>` 为什么不能随便 `add`？

示例回复：

因为 `List<?>` 里的 `?` 代表未知类型，你不知道这个列表真实接收的到底是什么类型。既然具体类型未知，编译器就不能允许你随便往里放对象，否则类型安全就被破坏了。

可以补一句更稳的结论：

- 一般可以安全读取成 `Object`
- 但不能安全写入任意具体对象

简单例子：

```java
List<?> list = new ArrayList<String>();
Object obj = list.get(0);
// list.add("abc"); // 编译报错
```

## 8. `? extends T` 和 `? super T` 有什么区别？

示例回复：

- `? extends T` 表示上界通配符，接收 `T` 或 `T` 的子类
- `? super T` 表示下界通配符，接收 `T` 或 `T` 的父类

它们最大的区别在于使用方向不同：

- `extends` 更适合读
- `super` 更适合写

## 9. 为什么说 `extends` 偏读、`super` 偏写？

示例回复：

因为 `List<? extends Number>` 里具体可能是 `Integer`、`Double` 等子类型，所以你往里写一个具体值并不安全；但读出来时，至少可以把它当 `Number` 用。  
而 `List<? super Integer>` 里至少能保证可以安全放入 `Integer`，因为它的元素类型是 `Integer` 的某个父类。

简单例子：

```java
List<? extends Number> a = new ArrayList<Integer>();
// a.add(1); // 不安全，编译报错
Number n = a.get(0);

List<? super Integer> b = new ArrayList<Number>();
b.add(1);
Object obj = b.get(0);
```

## 10. `List<Object>` 和 `List<String>` 是父子关系吗？

示例回复：

不是。虽然 `String` 是 `Object` 的子类，但 `List<String>` 不是 `List<Object>` 的子类。Java 的泛型在这里不是协变关系，否则类型安全会出问题。

可以顺带举一个反证：

如果 `List<String>` 能赋值给 `List<Object>`，那就可以往里面放 `Integer`，这样原本的 `String` 列表就被污染了。

## 11. 什么是类型擦除？

示例回复：

Java 泛型本质上主要服务于编译期。编译器在编译阶段会做类型检查，并在需要的地方插入强制转换；到了运行期，很多具体的泛型类型参数信息会被擦除掉，这就是类型擦除。

面试里一般说到这一步就够了，如果继续追问，再补：

- 这也是为什么很多泛型限制会存在
- 比如不能直接 `new T()`、不能直接创建泛型数组

## 12. 为什么不能直接 `new T()`？

示例回复：

因为在泛型代码里，`T` 只是一个类型参数，编译时知道这里有类型约束，但运行时很多具体类型信息已经不可直接拿来实例化了，所以不能直接写 `new T()`。

如果面试官继续追问，可以补充常见替代方案：

- 传入 `Class<T>`
- 传入工厂方法
- 传入 `Supplier<T>`

简单例子：

```java
class Factory<T> {
    private final Supplier<T> supplier;

    public Factory(Supplier<T> supplier) {
        this.supplier = supplier;
    }

    public T create() {
        return supplier.get();
    }
}
```

## 13. 为什么不能直接创建泛型数组？

示例回复：

因为数组在 Java 里会保留运行时类型信息，而泛型很多信息在运行时已经被擦除了。两者放在一起会有类型安全冲突，所以不能直接写 `new T[10]`。

面试里可以补一句更实用的说法：

- 一般更推荐直接用集合
- 如果确实要做，可以通过 `Object[]` 转、反射、或 `Array.newInstance` 处理

## 14. 为什么静态上下文不能直接用类上的泛型参数？

示例回复：

因为类上的泛型参数通常是跟随对象实例确定的，而静态成员属于类本身，不依赖某个具体实例。类都还没确定成什么类型参数，你就不能在静态上下文里直接使用这个实例级别的泛型参数。

错误示意：

```java
class Demo<T> {
    // private static T value; // 编译报错
}
```

## 15. 为什么不推荐使用原生类型，比如裸 `List`？

示例回复：

因为原生类型绕开了泛型带来的编译期检查，代码里会出现更多强制类型转换，也更容易把类型错误拖到运行时。面试里可以直接说：原生类型可用，但不推荐，除非是为了兼容旧代码。

## 16. 如果面试官问“你项目里泛型最常出现在哪”，可以怎么答？

示例回复：

项目里最常见的还是集合、通用返回体、工具类方法和一些通用接口定义。比如 `List<User>`、`Map<String, Object>`、分页结果 `PageResult<T>`、统一响应体 `Response<T>`，还有一些工具方法会写成泛型方法，提高复用性。

## 17. 一段比较稳的总回答

如果面试官让你整体讲一遍，可以这样说：

Java 泛型我一般从作用去理解，它主要是把类型检查前移到编译期，提高类型安全并减少强制类型转换。泛型常见在类、方法、接口三个位置。继续往下会遇到通配符 `?`、`? extends`、`? super`，其中 `extends` 更偏读，`super` 更偏写。再深一点，很多限制像 `new T()`、泛型数组、静态上下文不能直接用类上的泛型参数，本质上都和类型擦除有关。

## 18. 面试前最后背的结论

1. 泛型的核心价值是编译期类型检查
2. 泛型类、泛型方法、泛型接口要分层级理解
3. `?` 是未知类型，`extends` 偏读，`super` 偏写
4. `List<?>` 不能随便写入，是因为具体类型未知
5. 类型擦除是很多泛型限制背后的主线
6. `new T()`、泛型数组、静态泛型都是高频延伸题

## 19. 外部参考

- 牛客：快手客户端开发一面总结  
  https://www.nowcoder.com/discuss/741742919807250432
- 牛客：Java 八股大纲，很全！！  
  https://www.nowcoder.com/discuss/835134193616109568
- 牛客：java基础八股（上）  
  https://www.nowcoder.com/discuss/722234286346121216
