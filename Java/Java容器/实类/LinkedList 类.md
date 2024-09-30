---
tags:
  - Java
---
# LinkedList 类

## `LinkedList<E>` 类介绍

#### 继承层次结构

- `java.lang.Object`
- `java.util.AbstractCollection<E>`
- `java.util.AbstractList<E>`
- `java.util.AbstractSequentialList<E>`
- `java.util.LinkedList<E>`

**类结构**:

```java
public class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable
```

#### 1. 类型参数

- **E**: 此集合中保存的元素的类型。

#### 2. 继承与实现

- **继承**: `LinkedList` 继承自 `AbstractSequentialList<E>`。
- **实现的接口**: 
  - `Serializable`
  - `Cloneable`
  - `Iterable<E>`
  - `Collection<E>`
  - `Deque<E>`
  - `List<E>`
  - `Queue<E>`
  - `SequencedCollection<E>`

#### 3. 特性

- **双向链表**: `LinkedList` 是 `List` 和 `Deque` 接口的双向链表实现，支持从两端高效地插入和删除元素。
- **元素允许性**: 允许所有元素的存储，包括 `null` 值。
- **操作效率**: 所有操作的执行方式符合双向链表的预期。索引到列表的操作将根据指定的索引从列表的开始或结束进行遍历，以提高效率。

#### 4. 线程安全

- **非同步实现**: 此实现不是同步的。如果多个线程同时访问 `LinkedList`，且至少有一个线程对其进行了结构性修改（例如添加或删除元素），则必须在外部进行同步。
- **推荐同步方式**: 通常通过在自然封装列表的某个对象上进行同步。如果不存在这样的对象，建议使用 `Collections.synchronizedList` 方法来包装列表，以防止意外的非同步访问，例如：

  ```java
  List<E> list = Collections.synchronizedList(new LinkedList<E>());
  ```

#### 5. 迭代器

- **快速失败迭代器**: `LinkedList` 的 `iterator` 和 `listIterator` 方法返回的迭代器具有快速失败的特性。
  - 如果在创建迭代器后对列表进行了结构性修改（除非通过迭代器自身的 `remove` 或 `add` 方法），将抛出 `ConcurrentModificationException`。
  - 这种设计确保了在面对并发修改时，迭代器能够快速失败，而不是在未来的某个不确定时间表现出不确定的行为。

---

### `LinkedList<E>` 类构造函数和方法总结

#### 构造函数

| 构造函数 | 描述 |
|----------|------|
| `LinkedList()` | 构造一个空列表。 |
| `LinkedList(Collection<? extends E> c)` | 构造一个包含指定集合中元素的列表，顺序与集合的迭代器返回的顺序相同。 |

#### 方法摘要

| 修饰符和类型 | 方法 | 描述 |
|--------------|------|------|
| `void` | `add(int index, E element)` | 在列表中的指定位置插入指定元素。 |
| `boolean` | `add(E e)` | 将指定元素追加到此列表的末尾。 |
| `boolean` | `addAll(int index, Collection<? extends E> c)` | 将指定集合中的所有元素从指定位置开始插入到此列表中。 |
| `boolean` | `addAll(Collection<? extends E> c)` | 将指定集合中的所有元素追加到此列表的末尾，顺序与指定集合的迭代器返回的顺序相同。 |
| `void` | `addFirst(E e)` | 在此列表的开头插入指定元素。 |
| `void` | `addLast(E e)` | 将指定元素追加到此列表的末尾。 |
| `void` | `clear()` | 从此列表中移除所有元素。 |
| `Object` | `clone()` | 返回此 `LinkedList` 的浅拷贝。 |
| `boolean` | `contains(Object o)` | 如果此列表包含指定元素，则返回 `true`。 |
| `Iterator<E>` | `descendingIterator()` | 返回此双端队列中元素的逆序迭代器。 |
| `E` | `element()` | 检索但不移除此列表的头部（第一个元素）。 |
| `E` | `get(int index)` | 返回此列表中指定位置的元素。 |
| `E` | `getFirst()` | 返回此列表中的第一个元素。 |
| `E` | `getLast()` | 返回此列表中的最后一个元素。 |
| `int` | `indexOf(Object o)` | 返回此列表中指定元素的第一次出现的索引，如果此列表不包含该元素，则返回 -1。 |
| `int` | `lastIndexOf(Object o)` | 返回此列表中指定元素的最后一次出现的索引，如果此列表不包含该元素，则返回 -1。 |
| `ListIterator<E>` | `listIterator(int index)` | 返回此列表中元素的列表迭代器（按正确顺序），从列表中的指定位置开始。 |
| `boolean` | `offer(E e)` | 将指定元素作为此列表的尾部（最后一个元素）添加。 |
| `boolean` | `offerFirst(E e)` | 在此列表的开头插入指定元素。 |
| `boolean` | `offerLast(E e)` | 将指定元素追加到此列表的末尾。 |
| `E` | `peek()` | 检索但不移除此列表的头部（第一个元素）。 |
| `E` | `peekFirst()` | 检索但不移除此列表的第一个元素，如果此列表为空，则返回 `null`。 |
| `E` | `peekLast()` | 检索但不移除此列表的最后一个元素，如果此列表为空，则返回 `null`。 |
| `E` | `poll()` | 检索并移除此列表的头部（第一个元素）。 |
| `E` | `pollFirst()` | 检索并移除此列表的第一个元素，如果此列表为空，则返回 `null`。 |
| `E` | `pollLast()` | 检索并移除此列表的最后一个元素，如果此列表为空，则返回 `null`。 |
| `E` | `pop()` | 从此列表表示的堆栈中弹出一个元素。 |
| `void` | `push(E e)` | 将一个元素推送到此列表表示的堆栈中。 |
| `E` | `remove()` | 检索并移除此列表的头部（第一个元素）。 |
| `E` | `remove(int index)` | 移除此列表中指定位置的元素。 |
| `boolean` | `remove(Object o)` | 从此列表中移除指定元素的第一次出现（如果存在）。 |
| `E` | `removeFirst()` | 移除并返回此列表的第一个元素。 |
| `boolean` | `removeFirstOccurrence(Object o)` | 从此列表中移除指定元素的第一次出现（从头到尾遍历列表时）。 |
| `E` | `removeLast()` | 移除并返回此列表的最后一个元素。 |
| `boolean` | `removeLastOccurrence(Object o)` | 从此列表中移除指定元素的最后一次出现（从头到尾遍历列表时）。 |
| `LinkedList<E>` | `reversed()` | 返回此集合的逆序视图。 |
| `E` | `set(int index, E element)` | 用指定元素替换此列表中指定位置的元素。 |
| `int` | `size()` | 返回此列表中的元素数。 |
| `Spliterator<E>` | `spliterator()` | 创建一个延迟绑定和快速失败的此列表中元素的 `Spliterator`。 |
| `Object[]` | `toArray()` | 返回一个数组，其中包含此列表中所有元素的顺序（从第一个到最后一个元素）。 |
| `<T> T[]` | `toArray(T[] a)` | 返回一个数组，其中包含此列表中所有元素的顺序（从第一个到最后一个元素）；返回数组的运行时类型是指定数组的类型。 |

#### 其他方法

- **在 `java.util.AbstractSequentialList` 类中声明的方法**: `iterator`
- **在 `java.util.AbstractList` 类中声明的方法**: `equals`、`hashCode`、`listIterator`、`removeRange`、`subList`
- **在 `java.util.AbstractCollection` 类中声明的方法**: `containsAll`、`isEmpty`、`removeAll`、`retainAll`、`toString`
- **在 `java.lang.Object` 类中声明的方法**: `finalize`、`getClass`、`notify`、`notifyAll`、`wait`、`wait`、`wait`
- **在 `java.util.Collection` 接口中声明的方法**: `parallelStream`、`removeIf`、`stream`、`toArray`
- **在 `java.util.Deque` 接口中声明的方法**: `iterator`
- **在 `java.lang.Iterable` 接口中声明的方法**: `forEach`
- **在 `java.util.List` 接口中声明的方法**: `containsAll`、`equals`、`hashCode`、`isEmpty`、`iterator`、`listIterator`、`removeAll`、`replaceAll`、`retainAll`、`sort`、`subList`

---

#### 构造方法

1. **`LinkedList()`**
   - 无参构造函数，创建一个空的 `LinkedList` 实例。初始时列表中不包含任何元素。

2. **`LinkedList(Collection<? extends E> c)`**
   - 构造一个包含指定集合 `c` 中所有元素的 `LinkedList` 实例，元素的排列顺序与集合的迭代顺序相同。
   - **参数**：
     - `c`：要放入此列表中的元素的集合。
   - **抛出**：
     - `NullPointerException`：如果指定的集合为 `null`。

---

#### 常用方法

1. **元素操作**

   - **`getFirst()`**
     - 返回列表中的第一个元素。
     - **返回值**：列表中的第一个元素。
     - **抛出**：
       - `NoSuchElementException`：如果列表为空。

   - **`getLast()`**
     - 返回列表中的最后一个元素。
     - **返回值**：列表中的最后一个元素。
     - **抛出**：
       - `NoSuchElementException`：如果列表为空。

   - **`addFirst(E e)`**
     - 在列表的头部插入指定元素 `e`。
     - **参数**：`e` - 要添加的元素。

   - **`addLast(E e)`**
     - 在列表的尾部添加指定元素 `e`。此方法等效于 `add(E e)`。
     - **参数**：`e` - 要添加的元素。

   - **`removeFirst()`**
     - 移除并返回列表中的第一个元素。
     - **返回值**：列表中的第一个元素。
     - **抛出**：
       - `NoSuchElementException`：如果列表为空。

   - **`removeLast()`**
     - 移除并返回列表中的最后一个元素。
     - **返回值**：列表中的最后一个元素。
     - **抛出**：
       - `NoSuchElementException`：如果列表为空。

2. **查询操作**

   - **`size()`**
     - 返回列表中元素的数量。
     - **返回值**：列表中元素的数量。

   - **`contains(Object o)`**
     - 如果列表中包含指定元素 `o`，则返回 `true`。
     - **参数**：`o` - 要检查的元素。
     - **返回值**：`true`，如果列表中包含指定元素；否则返回 `false`。

   - **`indexOf(Object o)`**
     - 返回列表中指定元素 `o` 的第一次出现的索引位置，如果列表中不包含该元素，则返回 `-1`。
     - **参数**：`o` - 要搜索的元素。
     - **返回值**：指定元素的索引位置，如果列表中不包含该元素则返回 `-1`。

   - **`lastIndexOf(Object o)`**
     - 返回列表中指定元素 `o` 的最后一次出现的索引位置，如果列表中不包含该元素，则返回 `-1`。
     - **参数**：`o` - 要搜索的元素。
     - **返回值**：指定元素的最后一个索引位置，如果列表中不包含该元素则返回 `-1`。

3. **修改操作**

   - **`clear()`**
     - 从列表中移除所有元素，清空列表。

   - **`set(int index, E element)`**
     - 用指定元素 `element` 替换列表中指定位置的元素。
     - **参数**：
       - `index`：要替换的元素索引。
       - `element`：要存储在指定位置的元素。
     - **返回值**：先前在指定位置的元素。
     - **抛出**：
       - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index >= size()`）。

   - **`add(int index, E element)`**
     - 在指定位置插入元素 `element`。将当前位置及其后的元素向右移动。
     - **参数**：
       - `index`：要插入元素的索引。
       - `element`：要插入的元素。
     - **抛出**：
       - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index > size()`）。

   - **`remove(int index)`**
     - 删除列表中指定位置的元素，将后续元素向左移动。
     - **参数**：
       - `index`：要删除的元素索引。
     - **返回值**：先前在指定位置的元素。
     - **抛出**：
       - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index >= size()`）。

4. **堆栈操作**

   - **`push(E e)`**
     - 将元素 `e` 压入列表表示的栈，等效于 `addFirst(E)` 方法。
     - **参数**：`e` - 要推入的元素。

   - **`pop()`**
     - 弹出列表表示的栈中的元素，即移除并返回第一个元素。等效于 `removeFirst()` 方法。
     - **返回值**：列表的第一个元素。
     - **抛出**：
       - `NoSuchElementException`：如果列表为空。

5. **队列操作**

   - **`offer(E e)`**
     - 将指定元素添加到列表尾部。等效于 `add(E)`。
     - **参数**：`e` - 要添加的元素。
     - **返回值**：`true`，如果操作成功。

   - **`poll()`**
     - 检索并移除列表的头部（第一个元素）。如果列表为空，则返回 `null`。
     - **返回值**：列表的头部元素，如果列表为空则返回 `null`。

   - **`peek()`**
     - 检索但不移除列表的头部（第一个元素）。如果列表为空，则返回 `null`。
     - **返回值**：列表的头部元素，如果列表为空则返回 `null`。

6. **逆序视图**

   - **`reversed()`**
     - 返回列表的逆序视图，逆序操作影响所有对顺序敏感的操作，包括对返回视图的集合操作。对视图的修改会写入到原列表中。
     - **返回值**：逆序视图列表。

7. **迭代器**

   - **`listIterator(int index)`**
     - 返回一个列表迭代器，从指定位置 `index` 开始。
     - **参数**：`index` - 返回列表迭代器的起始位置。
     - **返回值**：从指定位置开始的 `ListIterator`。
     - **抛出**：
       - `IndexOutOfBoundsException`：如果索引超出范围（`index < 0 || index > size()`）。

   - **`descendingIterator()`**
     - 返回一个逆序迭代器，按照从尾部到头部的顺序遍历列表中的元素。
     - **返回值**：逆序迭代器。

8. **其他**

   - **`clone()`**
     - 返回 `LinkedList` 的浅拷贝（元素本身不会被克隆）。
     - **返回值**：`LinkedList` 实例的浅拷贝。

   - **`toArray()`**
     - 返回包含列表中所有元素的数组。
     - **返回值**：包含列表元素的数组。

---
