---
tags:
  - Java
---
# List接口

### `List<E>` 接口介绍

#### 类型参数

- **E**: 此列表中元素的类型。

#### 所有超接口

- `Collection<E>`
- `Iterable<E>`
- `SequencedCollection<E>`

#### 所有已知实现类

- `AbstractList`
- `AbstractSequentialList`
- `ArrayList`
- `AttributeList`
- `CopyOnWriteArrayList`
- `LinkedList`
- `RoleList`
- `RoleUnresolvedList`
- `Stack`
- `Vector`

---

| 修饰符和类型                             | 方法                                                     | 描述                                                                                                       |
|----------------------------------------|-------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `void`                                 | `add(int index, E element)`                           | 在列表中的指定位置插入指定的元素（可选操作）。                                                           |
| `boolean`                              | `add(E e)`                                           | 将指定的元素追加到此列表的末尾（可选操作）。                                                               |
| `boolean`                              | `addAll(int index, Collection<? extends E> c)`      | 将指定集合中的所有元素插入到列表的指定位置（可选操作）。                                                   |
| `boolean`                              | `addAll(Collection<? extends E> c)`                  | 将指定集合中的所有元素追加到列表的末尾，顺序与指定集合的迭代器返回的顺序相同（可选操作）。                   |
| `default void`                        | `addFirst(E e)`                                      | 将一个元素作为此集合的第一个元素添加（可选操作）。                                                         |
| `default void`                        | `addLast(E e)`                                       | 将一个元素作为此集合的最后一个元素添加（可选操作）。                                                      |
| `void`                                 | `clear()`                                            | 从列表中移除所有元素（可选操作）。                                                                         |
| `boolean`                              | `contains(Object o)`                                 | 如果此列表包含指定的元素，则返回 `true`。                                                                  |
| `boolean`                              | `containsAll(Collection<?> c)`                       | 如果此列表包含指定集合的所有元素，则返回 `true`。                                                         |
| `static <E> List<E>`                  | `copyOf(Collection<? extends E> coll)`               | 返回包含给定集合的元素的不可修改的列表，其迭代顺序与给定集合中的顺序相同。                                |
| `boolean`                              | `equals(Object o)`                                   | 将指定对象与此列表进行比较以检查相等性。                                                                   |
| `E`                                    | `get(int index)`                                     | 返回列表中指定位置的元素。                                                                                 |
| `default E`                           | `getFirst()`                                         | 获取此集合的第一个元素。                                                                                   |
| `default E`                           | `getLast()`                                          | 获取此集合的最后一个元素。                                                                                 |
| `int`                                  | `hashCode()`                                         | 返回此列表的哈希码值。                                                                                     |
| `int`                                  | `indexOf(Object o)`                                  | 返回此列表中指定元素的第一次出现的索引，如果此列表不包含该元素，则返回 `-1`。                           |
| `boolean`                              | `isEmpty()`                                          | 如果此列表不包含任何元素，则返回 `true`。                                                                  |
| `Iterator<E>`                          | `iterator()`                                         | 返回此列表中元素的迭代器，按正确顺序。                                                                     |
| `int`                                  | `lastIndexOf(Object o)`                              | 返回此列表中指定元素的最后一次出现的索引，如果此列表不包含该元素，则返回 `-1`。                        |
| `ListIterator<E>`                      | `listIterator()`                                     | 返回此列表中元素的列表迭代器（按正确顺序）。                                                              |
| `ListIterator<E>`                      | `listIterator(int index)`                            | 返回从列表中指定位置开始的元素的列表迭代器（按正确顺序）。                                               |
| `static <E> List<E>`                  | `of()`                                               | 返回一个包含零个元素的不可修改列表。                                                                        |
| `static <E> List<E>`                  | `of(E e1)`                                          | 返回一个包含一个元素的不可修改列表。                                                                        |
| `static <E> List<E>`                  | `of(E... elements)`                                  | 返回一个包含任意数量元素的不可修改列表。                                                                   |
| `static <E> List<E>`                  | `of(E e1, E e2)`                                    | 返回一个包含两个元素的不可修改列表。                                                                       |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3)`                              | 返回一个包含三个元素的不可修改列表。                                                                       |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3, E e4)`                        | 返回一个包含四个元素的不可修改列表。                                                                       |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3, E e4, E e5)`                  | 返回一个包含五个元素的不可修改列表。                                                                       |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3, E e4, E e5, E e6)`            | 返回一个包含六个元素的不可修改列表。                                                                       |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7)`      | 返回一个包含七个元素的不可修改列表。                                                                       |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8)`| 返回一个包含八个元素的不可修改列表。                                                                       |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9)` | 返回一个包含九个元素的不可修改列表。                                                                 |
| `static <E> List<E>`                  | `of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10)` | 返回一个包含十个元素的不可修改列表。                                                       |
| `E`                                    | `remove(int index)`                                 | 移除列表中指定位置的元素（可选操作）。                                                                     |
| `boolean`                              | `remove(Object o)`                                  | 从列表中移除指定元素的第一次出现（如果存在）（可选操作）。                                               |
| `boolean`                              | `removeAll(Collection<?> c)`                        | 从列表中删除包含在指定集合中的所有元素（可选操作）。                                                     |
| `default E`                           | `removeFirst()`                                     | 删除并返回此集合的第一个元素（可选操作）。                                                               |
| `default E`                           | `removeLast()`                                      | 删除并返回此集合的最后一个元素（可选操作）。                                                             |
| `default void`                        | `replaceAll(UnaryOperator<E> operator)`             | 用将运算符应用于该元素的结果替换此列表的每个元素。                                                       |
| `boolean`                              | `retainAll(Collection<?> c)`                        | 仅保留此列表中包含在指定集合中的元素（可选操作）。                                                       |
| `default List<E>`                    | `reversed()`                                        | 返回此集合的逆序视图。                                                                                   |
| `E`                                    | `set(int index, E element)`                         | 用指定元素替换此列表中指定位置的元素（可选操作）。                                                       |
| `int`                                  | `size()`                                            | 返回此列表中的元素数。                                                                                   |
| `default void`                        | `sort(Comparator<? super E> c)`                     | 根据指定的 Comparator 引起的顺序对此列表进行排序。                                                       |
| `default Spliterator<E>`              | `spliterator()`                                     | 在此列表中的元素上创建一个 Spliterator。                                                                 |
| `List<E>`                              | `subList(int fromIndex, int toIndex)`              | 返回此列表中从指定 `fromIndex`（包括）到 `toIndex`（不包括）的部分的视图。                               |
| `Object[]`                             | `toArray()`                                         | 返回一个包含此列表中所有元素的数组，按正确顺序排列（从第一个到最后一个元素）。                           |
| `<T> T[]`                             | `toArray(T[] a)`                                   | 返回一个包含此列表中所有元素的数组，按正确顺序排列（从第一个到最后一个元素）；返回的数组的运行时类型与指定数组的类型相同。 |

---

### `List<E>` 接口方法介绍

#### 1. `int size()`

- **描述**：返回此列表中的元素数量。如果此列表包含的元素超过 `Integer.MAX_VALUE` 个，则返回 `Integer.MAX_VALUE`。
- **返回**：此列表中的元素数。

---

#### 2. `boolean isEmpty()`

- **描述**：检查此列表是否为空。如果此列表不包含任何元素，则返回 `true`。
- **返回**：如果此列表不包含任何元素，则返回 `true`。

---

#### 3. `boolean contains(Object o)`

- **描述**：检查此列表是否包含指定的元素。如果此列表包含至少一个元素 `e`，使得 `Objects.equals(o, e)` 为 `true`，则返回 `true`。
- **参数**：`o` - 要测试其是否存在于此列表中的元素。
- **返回**：如果此列表包含指定的元素，则返回 `true`。
- **抛出**：
  - `ClassCastException`：如果指定元素的类型与此列表不兼容（可选）。
  - `NullPointerException`：如果指定元素为 `null` 且此列表不允许 `null` 元素（可选）。

---

#### 4. `Iterator<E> iterator()`

- **描述**：返回此列表中元素的迭代器，按正确顺序排列。
- **返回**：一个按正确顺序排列的此列表中元素的迭代器。

---

#### 5. `Object[] toArray()`

- **描述**：返回一个包含此列表中所有元素的数组，按正确顺序排列（从第一个到最后一个元素）。返回的数组将是“安全”的，即此列表不维护对它的任何引用。
- **返回**：一个包含此列表中所有元素的数组，按正确顺序排列。

---

#### 6. `<T> T[] toArray(T[] a)`

- **描述**：返回一个包含此列表中所有元素的数组，按正确顺序排列；返回的数组的运行时类型与指定数组的类型相同。如果列表适合指定的数组，则将其返回。否则，将使用指定数组的运行时类型和此列表的大小分配新数组。
- **参数**：`a` - 要存储此列表的元素的数组，如果足够大；否则，将为此目的分配相同运行时类型的新数组。
- **返回**：包含此列表的元素的数组。
- **抛出**：
  - `ArrayStoreException`：如果指定数组的运行时类型不是此列表中每个元素的运行时类型的超类型。
  - `NullPointerException`：如果指定数组为 `null`。

---

#### 7. `boolean add(E e)`

- **描述**：将指定的元素追加到此列表的末尾（可选操作）。
- **参数**：`e` - 要追加到此列表的元素。
- **返回**：`true`（如 `Collection.add(E)` 所指定）。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `add` 操作。
  - `ClassCastException`：如果指定元素的类阻止将其添加到此列表。
  - `NullPointerException`：如果指定元素为 `null` 且此列表不允许 `null` 元素。

---

#### 8. `boolean remove(Object o)`

- **描述**：从此列表中删除指定元素的第一次出现（可选操作）。如果此列表不包含该元素，则不会更改。
- **参数**：`o` - 如果存在，则从此列表中删除的元素。
- **返回**：`true` 如果此列表包含指定的元素。
- **抛出**：
  - `ClassCastException`：如果指定元素的类型与此列表不兼容（可选）。
  - `NullPointerException`：如果指定元素为 `null` 且此列表不允许 `null` 元素（可选）。
  - `UnsupportedOperationException`：如果此列表不支持 `remove` 操作。

---

#### 9. `boolean containsAll(Collection<?> c)`

- **描述**：检查此列表是否包含指定集合的所有元素。
- **参数**：`c` - 要在此列表中检查包含性的集合。
- **返回**：`true` 如果此列表包含指定集合的所有元素。
- **抛出**：
  - `ClassCastException`：如果指定集合中一个或多个元素的类型与此列表不兼容（可选）。
  - `NullPointerException`：如果指定集合包含一个或多个 `null` 元素且此列表不允许 `null` 元素（可选），或者指定集合为 `null`。

---

#### 10. `boolean addAll(Collection<? extends E> c)`

- **描述**：将指定集合中的所有元素按照其迭代器返回的顺序追加到此列表的末尾（可选操作）。
- **参数**：`c` - 包含要添加到此列表中的元素的集合。
- **返回**：`true` 如果此列表因调用而更改。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `addAll` 操作。
  - `ClassCastException`：如果指定集合的元素的类阻止将其添加到此列表中。
  - `NullPointerException`：如果指定集合包含一个或多个 `null` 元素且此列表不允许 `null` 元素，或者指定集合为 `null`。

---

#### 11. `boolean addAll(int index, Collection<? extends E> c)`

- **描述**：将指定集合中的所有元素按照其迭代器返回的顺序插入到此列表的指定位置（可选操作）。
- **参数**：
  - `index` - 要插入指定集合中第一个元素的索引。
  - `c` - 包含要添加到此列表中的元素的集合。
- **返回**：`true` 如果此列表因调用而更改。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `addAll` 操作。
  - `ClassCastException`：如果指定集合的元素的类阻止将其添加到此列表中。
  - `NullPointerException`：如果指定集合包含一个或多个 `null` 元素且此列表不允许 `null` 元素，或者指定集合为 `null`。
  - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index > size()`）。

---

#### 12. `boolean removeAll(Collection<?> c)`

- **描述**：从此列表中删除包含在指定集合中的所有元素（可选操作）。
- **参数**：`c` - 包含要从此列表中删除的元素的集合。
- **返回**：`true` 如果此列表因调用而更改。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `removeAll` 操作。
  - `ClassCastException`：如果此列表的一个元素的类与指定集合不兼容（可选）。
  - `NullPointerException`：如果此列表包含一个 `null` 元素且指定集合不允许 `null` 元素（可选），或者指定集合为 `null`。

---

#### 13. `boolean retainAll(Collection<?> c)`

- **描述**：仅保留此列表中包含在指定集合中的元素（可选操作）。
- **参数**：`c` - 包含要在此列表中保留的元素的集合。
- **返回**：`true` 如果此列表因调用而更改。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `retainAll` 操作。
  - `ClassCastException`：如果此列表的一个元素的类与指定集合不兼容（可选）。
  - `NullPointerException`：如果此列表包含一个 `null` 元素且指定集合不允许 `null` 元素（可选），或者指定集合为 `null`。

---

#### 14. `default void replaceAll(UnaryOperator<E> operator)`

- **描述**：将此列表的每个元素替换为将运算符应用于该元素的结果。
- **参数**：`operator` - 要应用于每个元素的操作符。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表是不可修改的。
  - `NullPointerException`：如果指定的操作符为 `null`。

---

#### 15. `default void sort(Comparator<? super E> c)`

- **描述**：根据指定的比较器对列表进行排序。排序是稳定的，确保相等元素的顺序不变。
- **参数**：`c` - 用于比较列表元素的比较器。
- **抛出**：
  - `ClassCastException`：如果列表包含使用指定比较器不相互比较的元素。
  - `UnsupportedOperationException`：如果列表的列表迭代器不支持 `set` 操作。
  - `IllegalArgumentException`：如果发现比较器违反了比较器的合同

。

---

#### 16. `void clear()`

- **描述**：从此列表中删除所有元素（可选操作）。此调用返回后，列表将为空。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `clear` 操作。

---

#### 17. `boolean equals(Object o)`

- **描述**：将指定对象与此列表进行比较以检查相等性。仅当指定对象也是一个列表时，两个列表具有相同的大小，并且两个列表中对应的元素对都是相等的时，才返回 `true`。
- **参数**：`o` - 用于与此列表比较相等性的对象。
- **返回**：如果指定对象等于此列表，则返回 `true`。

---

#### 18. `int hashCode()`

- **描述**：返回此列表的哈希码值。列表的哈希码定义为以下计算结果：

  ```java
  int hashCode = 1;
  for (E e : list)
      hashCode = 31 * hashCode + (e == null ? 0 : e.hashCode());
  ```

- **返回**：此列表的哈希码值。

---

#### 19. `E get(int index)`

- **描述**：返回此列表中指定位置的元素。
- **参数**：`index` - 要返回的元素的索引。
- **返回**：此列表中指定位置的元素。
- **抛出**：`IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index >= size()`）。

---

#### 20. `E set(int index, E element)`

- **描述**：用指定元素替换此列表中指定位置的元素（可选操作）。
- **参数**：
  - `index` - 要替换的元素的索引。
  - `element` - 要存储在指定位置的元素。
- **返回**：先前在指定位置的元素。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `set` 操作。
  - `ClassCastException`：如果指定元素的类阻止将其添加到此列表。
  - `NullPointerException`：如果指定元素为 `null` 且此列表不允许 `null` 元素。
  - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index >= size()`）。

---

#### 21. `void add(int index, E element)`

- **描述**：在此列表中指定位置插入指定元素（可选操作）。将当前在该位置的元素（如果有）和任何后续元素向右移动（将它们的索引加一）。
- **参数**：
  - `index` - 要插入指定元素的索引。
  - `element` - 要插入的元素。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `add` 操作。
  - `ClassCastException`：如果指定元素的类别阻止将其添加到此列表中。
  - `NullPointerException`：如果指定元素为 `null` 且此列表不允许 `null` 元素。
  - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index > size()`）。

---

#### 22. `E remove(int index)`

- **描述**：从此列表中指定位置移除元素（可选操作）。将任何后续元素向左移动（从它们的索引中减去一个）。
- **参数**：`index` - 要移除的元素的索引。
- **返回**：先前位于指定位置的元素。
- **抛出**：
  - `UnsupportedOperationException`：如果此列表不支持 `remove` 操作。
  - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index >= size()`）。

---

#### 23. `int indexOf(Object o)`

- **描述**：返回此列表中指定元素的第一次出现的索引，如果此列表不包含该元素，则返回 `-1`。
- **参数**：`o` - 要搜索的元素。
- **返回**：此列表中指定元素的第一次出现的索引，如果此列表不包含该元素，则返回 `-1`。
- **抛出**：
  - `ClassCastException`：如果指定元素的类型与此列表不兼容（可选）。
  - `NullPointerException`：如果指定元素为 `null` 且此列表不允许 `null` 元素（可选）。

---

#### 24. `int lastIndexOf(Object o)`

- **描述**：返回此列表中指定元素的最后一次出现的索引，如果此列表不包含该元素，则返回 `-1`。
- **参数**：`o` - 要搜索的元素。
- **返回**：此列表中指定元素的最后一次出现的索引，如果此列表不包含该元素，则返回 `-1`。
- **抛出**：
  - `ClassCastException`：如果指定元素的类型与此列表不兼容（可选）。
  - `NullPointerException`：如果指定元素为 `null` 且此列表不允许 `null` 元素（可选）。

---

#### 25. `ListIterator<E> listIterator()`

- **描述**：返回此列表中元素的列表迭代器（按正确顺序）。
- **返回**：此列表中元素的列表迭代器（按正确顺序）。

---

#### 26. `ListIterator<E> listIterator(int index)`

- **描述**：返回此列表中元素的列表迭代器（按正确顺序），从列表中指定位置开始。
- **参数**：`index` - 列表迭代器从中返回第一个元素的索引（通过调用 `next`）。
- **返回**：此列表中元素的列表迭代器（按正确顺序），从列表中指定位置开始。
- **抛出**：`IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index > size()`）。

---

#### 27. `List<E> subList(int fromIndex, int toIndex)`

- **描述**：返回此列表中指定 `fromIndex`（包括）和 `toIndex`（不包括）之间的部分视图。
- **参数**：
  - `fromIndex` - 子列表的低端点（包括）。
  - `toIndex` - 子列表的高端点（不包括）。
- **返回**：此列表中指定范围的视图。
- **抛出**：
  - `IndexOutOfBoundsException`：对于非法的端点索引值（`fromIndex < 0 || toIndex > size || fromIndex > toIndex`）。

---

#### 28. `default Spliterator<E> spliterator()`

- **描述**：在此列表中的元素上创建一个 `Spliterator`。
- **返回**：此列表中元素的 `Spliterator`。

---

#### 29. `default void addFirst(E e)`

- **描述**：将一个元素作为此集合的第一个元素添加（可选操作）。
- **参数**：`e` - 要添加的元素。
- **抛出**：
  - `NullPointerException`：如果指定元素为 `null` 且此集合不允许 `null` 元素。
  - `UnsupportedOperationException`：如果此集合实现不支持此操作。

---

#### 30. `default void addLast(E e)`

- **描述**：将一个元素作为此集合的最后一个元素添加（可选操作）。
- **参数**：`e` - 要添加的元素。
- **抛出**：
  - `NullPointerException`：如果指定元素为 `null` 且此集合不允许 `null` 元素。
  - `UnsupportedOperationException`：如果此集合实现不支持此操作。

---

#### 31. `default E getFirst()`

- **描述**：获取此集合的第一个元素。
- **返回**：检索到的元素。
- **抛出**：
  - `NoSuchElementException`：如果此集合为空。

---

#### 32. `default E getLast()`

- **描述**：获取此集合的最后一个元素。
- **返回**：检索到的元素。
- **抛出**：
  - `NoSuchElementException`：如果此集合为空。

---

#### 33. `default E removeFirst()`

- **描述**：移除并返回此集合的第一个元素（可选操作）。
- **返回**：移除的元素。
- **抛出**：
  - `NoSuchElementException`：如果此集合为空。
  - `UnsupportedOperationException`：如果此集合实现不支持此操作。

---

#### 34. `default E removeLast()`

- **描述**：移除并返回此集合的最后一个元素（可选操作）。
- **返回**：移除的元素。
- **抛出**：
  - `NoSuchElementException`：如果此集合为空。
  - `UnsupportedOperationException`：如果此集合实现不支持此操作。

---

#### 35. `default List<E> reversed()`

- **描述**：

返回此集合的逆序视图。返回视图中元素的遭遇顺序与此集合中元素的遭遇顺序相反。

- **返回**：此集合的逆序视图，作为一个 `List`。

---

#### 36. `static <E> List<E> of(E... elements)`

- **描述**：返回一个包含任意数量元素的不可修改列表。
- **参数**：`elements` - 要包含在列表中的元素。
- **返回**：包含指定元素的 `List`。
- **抛出**：
  - `NullPointerException`：如果元素为 `null` 或数组为 `null`。

---

#### 37. `static <E> List<E> copyOf(Collection<? extends E> coll)`

- **描述**：返回一个包含给定集合元素的不可修改列表，顺序与其迭代顺序相同。
- **参数**：`coll` - 从中提取元素的集合，必须非 `null`。
- **返回**：包含给定集合元素的 `List`。
- **抛出**：
  - `NullPointerException`：如果 `coll` 为 `null`，或者它包含任何 `null` 值。

---
