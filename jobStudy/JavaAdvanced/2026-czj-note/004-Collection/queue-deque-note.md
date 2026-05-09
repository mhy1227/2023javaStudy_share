# Queue 与 Deque 基础笔记

## 1. 为什么集合里还要单独学 Queue

前面我们已经见过：

- `List`
- `Set`

但在实际开发里，还有一类很重要的需求是：

- 按队列方式管理元素

这就会用到：

- `Queue`
- `Deque`

## 2. 什么是 Queue

`Queue` 可以先理解成：

- 队列

最经典的理解是：

- 先进先出

也就是常说的：

- FIFO

## 3. Queue 的常见使用场景

例如：

- 排队处理任务
- 按顺序消费数据
- 广度优先遍历

## 4. 什么是 Deque

`Deque` 是：

- 双端队列

也就是说：

- 两头都可以插入
- 两头都可以删除

所以它比普通 `Queue` 更灵活。

## 5. Queue 和 Deque 的关系

可以简单记成：

- `Deque` 是更灵活的队列接口

它既可以表现成：

- 普通队列

也可以表现成：

- 类似栈的结构

## 6. 常见实现类

当前阶段先认识这几个：

- `LinkedList`
- `ArrayDeque`
- `PriorityQueue`

## 7. LinkedList 在这里为什么又出现了

因为 `LinkedList` 不只是一个 `List`。

它还可以作为：

- `Deque`

来使用。

所以 `LinkedList` 在集合章节里经常“一物多用”。

## 8. ArrayDeque

可以先记：

- 常见的双端队列实现

适合：

- 队列
- 双端操作

## 9. PriorityQueue

这个类比较特别。

它不是单纯按插入顺序出队，而是更偏：

- 优先级出队

所以它经常和：

- 优先级任务
- 堆

这种话题连在一起。

当前阶段只需先知道它和普通 FIFO 队列不同。

## 10. Queue / Deque 常见方法

当前阶段先记几个高频方法：

- `offer()`
- `poll()`
- `peek()`

大致理解：

- `offer()`：入队
- `poll()`：出队并返回元素
- `peek()`：查看队头但不删除

如果是 `Deque`，还常见：

- `offerFirst()`
- `offerLast()`
- `pollFirst()`
- `pollLast()`

## 11. 当前阶段最该记住的结论

1. `Queue` 更偏队列语义
2. `Deque` 是双端队列
3. `LinkedList` 既能做 `List`，也能做 `Deque`
4. `PriorityQueue` 更偏优先级，不是普通先进先出

## 12. 一句话总结

如果 `List` 是“按顺序放一批数据”，那 `Queue/Deque` 更像“按出入规则管理一批数据”。
