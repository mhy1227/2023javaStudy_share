# LinkedHashMap 单体笔记

## 1. LinkedHashMap 是什么

`LinkedHashMap` 可以先理解成：

- 在 `HashMap` 基础上更强调顺序表现的 `Map`

## 2. 核心特点

- 存 `key-value`
- key 不能重复
- 顺序表现更稳定

## 3. 它适合什么场景

适合这些需求：

- 既想用 `Map`
- 又希望遍历顺序更可控

## 4. 为什么值得单独记

因为它经常被拿来和：

- `HashMap`
- `TreeMap`

做横向对比。

## 5. 当前阶段注意点

- 它不是最常见主力
- 但在“映射 + 顺序”并存时很常见

## 6. 一句话总结

`LinkedHashMap` 是“带顺序表现的 Map”。
