---
tags:
  - Java
---
# Set接口

### `Set<E>` 接口介绍

#### 类型参数

- **E**: 此集合中包含的元素的类型。

#### 所有超接口

- `Collection<E>`
- `Iterable<E>`

#### 所有已知子接口

- `EventSet`
- `NavigableSet<E>`
- `SequencedSet<E>`
- `SortedSet<E>`

#### 所有已知实现类

- `AbstractSet`
- `ConcurrentHashMap.KeySetView`
- `ConcurrentSkipListSet`
- `CopyOnWriteArraySet`
- `EnumSet`
- `HashSet`
- `JobStateReasons`
- `LinkedHashSet`
- `TreeSet`

#### 描述

`Set<E>` 接口定义了一个不包含重复元素的集合。更正式地说，集合不包含任何一对元素 `e1` 和 `e2`，使得 `e1.equals(e2)` 为 `true`，并且最多包含一个空元素。正如其名称所暗示的，此接口模拟了数学中的集合抽象概念。

- **契约规定**：`Set` 接口对所有构造函数的契约以及 `add`、`equals` 和 `hashCode` 方法的契约施加了额外的规定，超出了从 `Collection` 接口继承的规定。其他继承方法的声明也包括在此处以方便查阅。

- **构造函数的额外规定**：所有构造函数必须创建一个不包含重复元素的集合（如上所定义）。

---

| 修饰符和类型                             | 方法                                                     | 描述                                                                                                       |
|----------------------------------------|-------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `boolean`                              | `add(E e)`                                           | 将指定的元素添加到此集合中（可选操作）。                                                                  |
| `boolean`                              | `addAll(Collection<? extends E> c)`                  | 将指定集合中的所有元素添加到此集合中（可选操作）。                                                        |
| `void`                                 | `clear()`                                            | 从此集合中移除所有元素（可选操作）。                                                                      |
| `boolean`                              | `contains(Object o)`                                 | 如果此集合包含指定的元素，则返回 `true`。                                                                |
| `boolean`                              | `containsAll(Collection<?> c)`                       | 如果此集合包含指定集合的所有元素，则返回 `true`。                                                        |
| `static <E> Set<E>`                   | `copyOf(Collection<? extends E> coll)`               | 返回包含给定集合的元素的不可修改的 `Set`。                                                                |
| `boolean`                              | `equals(Object o)`                                   | 将指定对象与此集合进行比较以测试相等性。                                                                  |
| `int`                                  | `hashCode()`                                         | 返回此集合的哈希码值。                                                                                     |
| `boolean`                              | `isEmpty()`                                          | 如果此集合不包含任何元素，则返回 `true`。                                                                |
| `Iterator<E>`                          | `iterator()`                                         | 返回此集合中元素的迭代器。                                                                                |
| `static <E> Set<E>`                   | `of()`                                               | 返回一个包含零个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1)`                                          | 返回一个包含一个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E... elements)`                                  | 返回一个包含任意数量元素的不可修改集合。                                                                  |
| `static <E> Set<E>`                   | `of(E e1, E e2)`                                    | 返回一个包含两个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3)`                              | 返回一个包含三个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3, E e4)`                        | 返回一个包含四个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3, E e4, E e5)`                  | 返回一个包含五个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3, E e4, E e5, E e6)`            | 返回一个包含六个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7)`      | 返回一个包含七个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8)`| 返回一个包含八个元素的不可修改集合。                                                                      |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9)` | 返回一个包含九个元素的不可修改集合。                                                                |
| `static <E> Set<E>`                   | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10)` | 返回一个包含十个元素的不可修改集合。                                                        |
| `boolean`                              | `remove(Object o)`                                  | 如果存在，则从此集合中移除指定的元素（可选操作）。                                                        |
| `boolean`                              | `removeAll(Collection<?> c)`                        | 从此集合中移除包含在指定集合中的所有元素（可选操作）。                                                  |
| `boolean`                              | `retainAll(Collection<?> c)`                        | 仅保留此集合中包含在指定集合中的元素（可选操作）。                                                      |
| `int`                                  | `size()`                                            | 返回此集合中的元素数量（基数）。                                                                          |
| `default Spliterator<E>`              | `spliterator()`                                     | 在此集合中的元素上创建一个 `Spliterator`。                                                                |
| `Object[]`                             | `toArray()`                                         | 返回一个包含此集合中所有元素的数组。                                                                      |
| `<T> T[]`                             | `toArray(T[] a)`                                   | 返回一个包含此集合中所有元素的数组；返回数组的运行时类型是指定数组的类型。                             |

---

### `Set<E>` 接口方法介绍

#### 1. `int size()`

- **描述**：返回此集合中的元素数量（基数）。如果此集合包含的元素超过 `Integer.MAX_VALUE` 个，则返回 `Integer.MAX_VALUE`。
- **指定者**：`size` 在接口 `Collection<E>` 中。

---

#### 2. `boolean isEmpty()`

- **描述**：如果此集合不包含任何元素，则返回 `true`。
- **指定者**：`isEmpty` 在接口 `Collection<E>` 中。

---

#### 3. `boolean contains(Object o)`

- **描述**：如果此集合包含指定的元素，则返回 `true`。更正式地说，如果此集合包含使 `Objects.equals(o, e)` 为 `true` 的元素 `e`，则返回 `true`。
- **指定者**：`contains` 在接口 `Collection<E>` 中。
- **参数**：
  - `o` - 要测试其是否存在于此集合中的元素。
- **抛出**：
  - `ClassCastException` - 如果指定元素的类型与此集合不兼容（可选）。
  - `NullPointerException` - 如果指定元素为 `null` 且此集合不允许 `null` 元素（可选）。

---

#### 4. `Iterator<E> iterator()`

- **描述**：返回此集合中元素的迭代器。元素以无特定顺序返回（除非此集合是某个提供保证的类的实例）。
- **指定者**：`iterator` 在接口 `Collection<E>` 中和 `Iterable<E>` 中。

---

#### 5. `Object[] toArray()`

- **描述**：返回一个包含此集合中所有元素的数组。如果此集合对其元素的返回顺序有任何保证，那么此方法必须以相同顺序返回元素。
- **指定者**：`toArray` 在接口 `Collection<E>` 中。

---

#### 6. `<T> T[] toArray(T[] a)`

- **描述**：返回一个包含此集合中所有元素的数组；返回数组的运行时类型与指定数组的类型相同。如果集合适合于指定的数组，则将其返回。否则，将使用指定数组的运行时类型和此集合的大小分配一个新数组。
- **指定者**：`toArray` 在接口 `Collection<E>` 中。
- **参数**：
  - `a` - 如果足够大，则将此集合的元素存储到其中的数组；否则，将为此目的分配相同运行时类型的新数组。
- **抛出**：
  - `ArrayStoreException` - 如果指定数组的运行时类型不是此集合中每个元素的运行时类型的超类型。
  - `NullPointerException` - 如果指定数组为 `null`。

---

#### 7. `boolean add(E e)`

- **描述**：如果尚未存在，则将指定的元素添加到此集合（可选操作）。如果集合不包含 `Objects.equals(e, e2)` 的元素 `e`，则将指定的元素 `e` 添加到此集合。如果此集合已包含该元素，则调用将保持集合不变并返回 `false`。
- **指定者**：`add` 在接口 `Collection<E>` 中。
- **参数**：
  - `e` - 要添加到此集合的元素。
- **抛出**：
  - `UnsupportedOperationException` - 如果此集合不支持 `add` 操作。
  - `ClassCastException` - 如果指定元素的类阻止将其添加到此集合。
  - `NullPointerException` - 如果指定元素为 `null` 且此集合不允许 `null` 元素。
  - `IllegalArgumentException` - 如果指定元素的某些属性阻止将其添加到此集合。

---

#### 8. `boolean remove(Object o)`

- **描述**：如果存在，则从此集合中删除指定的元素（可选操作）。如果此集合包含 `Objects.equals(o, e)` 的元素 `e`，则删除该元素。如果此集合包含该元素，则返回 `true`（或者等效地，如果此集合由于调用而更改）。
- **指定者**：`remove` 在接口 `Collection<E>` 中。
- **参数**：
  - `o` - 如果存在，则从此集合中删除的对象。
- **抛出**：
  - `ClassCastException` - 如果指定元素的类型与此集合不兼容（可选）。
  - `NullPointerException` - 如果指定元素为 `null` 且此集合不允许 `null` 元素（可选）。
  - `UnsupportedOperationException` - 如果此集合不支持 `remove` 操作。

---

#### 9. `boolean containsAll(Collection<?> c)`

- **描述**：如果此集合包含指定集合的所有元素，则返回 `true`。
- **指定者**：`containsAll` 在接口 `Collection<E>` 中。
- **参数**：
  - `c` - 要检查其是否包含在此集合中的集合。
- **抛出**：
  - `ClassCastException` - 如果指定集合中一个或多个元素的类型与此集合不兼容（可选）。
  - `NullPointerException` - 如果指定集合包含一个或多个 `null` 元素且此集合不允许 `null` 元素（可选），或者指定集合为 `null`。

---

#### 10. `boolean addAll(Collection<? extends E> c)`

- **描述**：如果尚未存在，则将指定集合中的所有元素添加到此集合（可选操作）。如果指定的集合也是一个集合，则 `addAll` 操作有效地修改此集合，使其值为两个集合的并集。
- **指定者**：`addAll` 在接口 `Collection<E>` 中。
- **参数**：
  - `c` - 包含要添加到此集合中的元素的集合。
- **返回值**：如果调用导致此集合发生更改，则返回 `true`。
- **抛出**：
  - `UnsupportedOperationException` - 如果此集合不支持 `addAll` 操作。
  - `ClassCastException` - 如果指定集合的元素的类别阻止将其添加到此集合中。
  - `NullPointerException` - 如果指定集合包含一个或多个 `null` 元素且此集合不允许 `null` 元素，或者指定集合为 `null`。
  - `IllegalArgumentException` - 如果指定集合的元素的某些属性阻止将其添加到此集合中。

---

#### 11. `boolean retainAll(Collection<?> c)`

- **描述**：仅保留此集合中包含在指定集合中的元素（可选操作）。
- **指定者**：`retainAll` 在接口 `Collection<E>` 中。
- **参数**：
  - `c` - 包含要保留在此集合中的元素的集合。
- **返回值**：如果调用导致此集合发生更改，则返回 `true`。
- **抛出**：
  - `UnsupportedOperationException` - 如果此集合不支持 `retainAll` 操作。
  - `ClassCastException` - 如果此集合的元素的类别与指定集合不兼容（可选）。
  - `NullPointerException` - 如果此集合包含 `null` 元素且指定集合不允许 `null` 元素（可选），或者指定集合为 `null`。

---

#### 12. `boolean removeAll(Collection<?> c)`

- **描述**：从此集合中删除包含在指定集合中的所有元素（可选操作）。
- **指定者**：`removeAll` 在接口 `Collection<E>` 中。
- **参数**：
  - `c` - 包含要从此集合中删除的元素的集合。
- **返回值**：如果调用导致此集合发生更改，则返回 `true`。
- **抛出**：
  - `UnsupportedOperationException` - 如果此集合不支持 `removeAll` 操作。
  - `ClassCastException` - 如果此集合的元素的类别与指定集合不兼容（可选）。
  - `NullPointerException` - 如果此集合包含 `null` 元素且指定集合不允许 `null` 元素（可选），或者指定集合为 `null`。

---

#### 13. `void clear()`

- **描述**：从此集合中删除所有元素（可选操作）。此调用返回后，集合将为空。
- **指定者**：`clear` 在接口 `Collection<E>` 中。
- **抛出**：
  - `UnsupportedOperationException` - 如果此集合不支持 `clear` 方法。

---

#### 14. `boolean equals(Object o)`

- **描述**：将指定对象与此集合进行比较以检查是否相等。
- **指定者**：`equals` 在接口 `Collection<E>` 中。
- **参数**：
  - `o` - 用于与此集合比较相等的对象。
- **返回值**：如果指定对象等于此集合，则返回 `true`。

---

#### 15. `int hashCode()`

- **描述**：返回此集合的哈希码值。集合的哈希码定义为集合中元素的哈希码之和，其中 `null` 元素的哈希码定义为零。

- **指定者**：`hashCode` 在接口 `Collection<E>` 中。

---

#### 16. `default Spliterator<E> spliterator()`

- **描述**：在此集合中的元素上创建一个 `Spliterator`。
- **指定者**：`spliterator` 在接口 `Collection<E>` 中和 `Iterable<E>` 中。

---

#### 17. `static <E> Set<E> of()`

- **描述**：返回一个包含零个元素的不可修改集合。
- **返回值**：一个空的 `Set`。

---

#### 18. `static <E> Set<E> of(E e1)`

- **描述**：返回一个包含一个元素的不可修改集合。
- **参数**：
  - `e1` - 单个元素。

---

#### 19. `static <E> Set<E> of(E e1, E e2)`

- **描述**：返回一个包含两个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。

---

#### 20. `static <E> Set<E> of(E e1, E e2, E e3)`

- **描述**：返回一个包含三个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。

---

#### 21. `static <E> Set<E> of(E e1, E e2, E e3, E e4)`

- **描述**：返回一个包含四个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。
  - `e4` - 第四个元素。

---

#### 22. `static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5)`

- **描述**：返回一个包含五个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。
  - `e4` - 第四个元素。
  - `e5` - 第五个元素。

---

#### 23. `static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6)`

- **描述**：返回一个包含六个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。
  - `e4` - 第四个元素。
  - `e5` - 第五个元素。
  - `e6` - 第六个元素。

---

#### 24. `static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7)`

- **描述**：返回一个包含七个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。
  - `e4` - 第四个元素。
  - `e5` - 第五个元素。
  - `e6` - 第六个元素。
  - `e7` - 第七个元素。

---

#### 25. `static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8)`

- **描述**：返回一个包含八个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。
  - `e4` - 第四个元素。
  - `e5` - 第五个元素。
  - `e6` - 第六个元素。
  - `e7` - 第七个元素。
  - `e8` - 第八个元素。

---

#### 26. `static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9)`

- **描述**：返回一个包含九个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。
  - `e4` - 第四个元素。
  - `e5` - 第五个元素。
  - `e6` - 第六个元素。
  - `e7` - 第七个元素。
  - `e8` - 第八个元素。
  - `e9` - 第九个元素。

---

#### 27. `static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10)`

- **描述**：返回一个包含十个元素的不可修改集合。
- **参数**：
  - `e1` - 第一个元素。
  - `e2` - 第二个元素。
  - `e3` - 第三个元素。
  - `e4` - 第四个元素。
  - `e5` - 第五个元素。
  - `e6` - 第六个元素。
  - `e7` - 第七个元素。
  - `e8` - 第八个元素。
  - `e9` - 第九个元素。
  - `e10` - 第十个元素。

---

#### 28. `@SafeVarargs static <E> Set<E> of(E... elements)`

- **描述**：返回一个包含任意数量元素的不可修改集合。此方法还接受单个数组作为参数。结果集的元素类型将是数组的组件类型，并且集合的大小将等于数组的长度。
- **参数**：
  - `elements` - 要包含在集合中的元素。
- **抛出**：
  - `IllegalArgumentException` - 如果存在任何重复元素。
  - `NullPointerException` - 如果元素为 `null` 或者数组为 `null`。

---

#### 29. `static <E> Set<E> copyOf(Collection<? extends E> coll)`

- **描述**：返回一个包含给定集合元素的不可修改集合。给定集合不能为空，并且不能包含任何 `null` 元素。
- **参数**：
  - `coll` - 从中提取元素的 `Collection`，必须非空。
- **抛出**：
  - `NullPointerException` - 如果 `coll` 为 `null`，或者包含任何 `null` 值。

---
