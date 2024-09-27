### `ArrayList<E>` 类介绍

#### 概述

`ArrayList<E>` 是 `List` 接口的可调整大小数组实现。它允许包括 `null` 在内的所有元素，并实现了所有可选的列表操作。与 `Vector` 类似，但 `ArrayList` 是不同步的。该类提供了对内部用于存储列表的数组大小的操作。

- **类型参数**：`E` - 此列表中元素的类型。
- **直接已知的子类**：`AttributeList`, `RoleList`, `RoleUnresolvedList`.

#### 性能特性

- `size`, `isEmpty`, `get`, `set`, `iterator` 和 `listIterator` 操作在常数时间内运行。
- `add` 操作在摊销的常数时间内运行，添加 `n` 个元素需要 `O(n)` 的时间。
- 所有其他操作在线性时间内运行（粗略地说）。

#### 容量管理

- 每个 `ArrayList` 实例都有一个容量，它是用于存储列表中元素的数组的大小。容量始终至少与列表大小一样大。
- 当元素添加到 `ArrayList` 时，容量会自动增长。
- 应用程序可以在向 `ArrayList` 实例添加大量元素之前使用 `ensureCapacity` 方法增加容量，以减少逐步重新分配的数量。

#### 同步性

- `ArrayList` 实现不是同步的。如果多个线程同时访问一个 `ArrayList` 实例，并且至少有一个线程在结构上修改列表，则必须在外部同步它。
    
- 通常通过在自然封装列表的某个对象上同步来实现这一点。如果不存在这样的对象，则应在创建时使用 `Collections.synchronizedList` 方法“包装”列表：

```java
    List list = Collections.synchronizedList(new ArrayList<>(...));
```

#### 迭代器

- 此类的 `iterator` 和 `listIterator` 方法返回的迭代器是快速失败的。如果在创建迭代器后的任何时间内以任何方式对列表进行结构修改（除了通过迭代器自身的 `remove` 或 `add` 方法），迭代器将抛出 `ConcurrentModificationException`。
- 快速失败的迭代器旨在在面对并发修改时快速且清晰地失败，而不是在未来的某个不确定时间冒险进行非确定性的行为。

---

### 字段摘要

- **modCount**
  - **描述**：此字段用于记录列表的修改次数，主要用于快速失败的迭代器机制。每当结构性修改（如添加或删除元素）发生时，该值会增加。这使得在迭代过程中检测并发修改成为可能。

---

### 构造方法摘要

1. **ArrayList()**
   - **描述**：构造一个具有初始容量为十的空列表。
   - **示例**：

     ```java
     ArrayList<String> list = new ArrayList<>();
     ```

2. **ArrayList(int initialCapacity)**
   - **描述**：构造一个具有指定初始容量的空列表。这对于避免在添加大量元素时频繁的重新分配非常有用。
   - **参数**：
     - `initialCapacity` - 列表的初始容量。
   - **示例**：

     ```java
     ArrayList<String> list = new ArrayList<>(50);
     ```

3. **`ArrayList(Collection<? extends E> c)`**
   - **描述**：构造一个包含指定集合元素的列表，顺序与集合的迭代器返回的顺序相同。这种构造方法使得可以轻松地将现有集合转换为 `ArrayList`。
   - **参数**：
     - `c` - 包含要添加到列表中的元素的集合。
   - **示例**：

     ```java
     List<String> originalList = Arrays.asList("A", "B", "C");
     ArrayList<String> list = new ArrayList<>(originalList);
     ```

---

### 构造函数详情

| 构造函数                                            | 描述                                                                               |
|---------------------------------------------------|-----------------------------------------------------------------------------------|
| `ArrayList()`                                     | 构造一个具有初始容量为十的空列表。                                                |
| `ArrayList(int initialCapacity)`                  | 构造一个具有指定初始容量的空列表。<br>**参数:**<br>`initialCapacity` - 列表的初始容量。<br>**抛出:**<br>IllegalArgumentException - 如果指定的初始容量为负数。 |
| `ArrayList(Collection<? extends E> c)`           | 构造一个包含指定集合元素的列表，顺序与集合的迭代器返回的顺序相同。<br>**参数:**<br>`c` - 要放入此列表中的元素的集合。<br>**抛出:**<br>NullPointerException - 如果指定的集合为null。 |

### 方法详情

| 修饰符和类型                | 方法                                         | 描述                                                                                                   |
|-----------------------------|---------------------------------------------|--------------------------------------------------------------------------------------------------------|
| void                        | `trimToSize()`                             | 将此 `ArrayList` 实例的容量调整为列表的当前大小。                                                     |
| void                        | `ensureCapacity(int minCapacity)`          | 如有必要，增加此 `ArrayList` 实例的容量，以确保其至少可以容纳由最小容量参数指定的元素数量。        |
| int                         | `size()`                                   | 返回此列表中的元素数。                                                                                 |
| boolean                     | `isEmpty()`                                | 如果此列表不包含任何元素，则返回 `true`。                                                             |
| boolean                     | `contains(Object o)`                       | 如果此列表包含指定元素，则返回 `true`。                                                               |
| int                         | `indexOf(Object o)`                        | 返回此列表中指定元素的第一次出现的索引；如果不包含该元素，则返回 -1。                                   |
| int                         | `lastIndexOf(Object o)`                    | 返回此列表中指定元素的最后一次出现的索引；如果不包含该元素，则返回 -1。                               |
| Object                      | `clone()`                                  | 返回此 `ArrayList` 实例的浅拷贝。（元素本身不会被复制。）                                             |
| Object[]                   | `toArray()`                                | 返回一个数组，其中包含此列表中所有元素的正确顺序（从第一个到最后一个元素）。                           |
| <T> T[]                    | `toArray(T[] a)`                          | 返回一个数组，其中包含此列表中所有元素的正确顺序；返回数组的运行时类型与指定数组的类型相同。         |
| E                           | `get(int index)`                           | 返回此列表中指定位置的元素。                                                                             |
| E                           | `getFirst()`                               | 获取此集合的第一个元素。                                                                                 |
| E                           | `getLast()`                                | 获取此集合的最后一个元素。                                                                               |
| E                           | `set(int index, E element)`                | 用指定元素替换此列表中指定位置的元素。                                                                  |
| boolean                     | `add(E e)`                                 | 将指定元素追加到此列表的末尾。                                                                          |
| void                        | `add(int index, E element)`                | 在此列表中指定位置插入指定元素。将当前在该位置的元素（如果有）和任何后续元素向右移动（增加它们的索引）。 |
| void                        | `addFirst(E element)`                      | 将元素添加为此集合的第一个元素（可选操作）。                                                            |
| void                        | `addLast(E element)`                       | 将元素添加为此集合的最后一个元素（可选操作）。                                                          |
| E                           | `remove(int index)`                        | 删除此列表中指定位置的元素。                                                                             |
| E                           | `removeFirst()`                            | 删除并返回此集合的第一个元素（可选操作）。                                                              |
| E                           | `removeLast()`                             | 删除并返回此集合的最后一个元素（可选操作）。                                                            |
| boolean                     | `remove(Object o)`                         | 从此列表中删除指定元素的第一个出现，如果存在的话。                                                      |
| void                        | `clear()`                                  | 从此列表中删除所有元素。                                                                                 |
| boolean                     | `addAll(Collection<? extends E> c)`       | 将指定集合中的所有元素按照它们由指定集合的迭代器返回的顺序追加到此列表的末尾。                         |
| boolean                     | `addAll(int index, Collection<? extends E> c)` | 将指定集合中的所有元素从指定位置开始插入到此列表中。                                                  |
| boolean                     | `removeAll(Collection<?> c)`               | 从此列表中删除包含在指定集合中的所有元素。                                                             |
| boolean                     | `retainAll(Collection<?> c)`               | 仅保留此列表中包含在指定集合中的元素。                                                                 |
| ListIterator<E>            | `listIterator(int index)`                  | 返回一个列表迭代器，该迭代器按正确顺序遍历此列表中的元素，从列表中的指定位置开始。                      |
| ListIterator<E>            | `listIterator()`                           | 返回一个列表迭代器，该迭代器按正确顺序遍历此列表中的元素。                                             |
| Iterator<E>                | `iterator()`                               | 返回一个迭代器，该迭代器按正确顺序遍历此列表中的元素。                                               |
| List<E>                    | `subList(int fromIndex, int toIndex)`    | 返回此列表中指定的 `fromIndex`（包括）到 `toIndex`（不包括）之间的部分视图。                            |
| void                        | `forEach(Consumer<? super E> action)`     | 对 `Iterable` 的每个元素执行给定操作，直到所有元素都已处理或操作引发异常。                              |
| Spliterator<E>             | `spliterator()`                            | 创建一个在此列表中的元素上进行延迟绑定和快速失败的 `Spliterator`。                                      |
| boolean                     | `removeIf(Predicate<? super E> filter)`   | 删除满足给定谓词的此集合的所有元素。                                                                    |

---

## 构造方法

- **`ArrayList(int initialCapacity)`**
  - 构造一个具有指定初始容量的空列表。
  - **参数:**
    - `initialCapacity` - 列表的初始容量
  - **抛出:**
    - `IllegalArgumentException` - 如果指定的初始容量为负数

- **`ArrayList()`**
  - 构造一个具有初始容量为十的空列表。

- **`ArrayList(Collection<? extends E> c)`**
  - 构造一个包含指定集合元素的列表，顺序与集合的迭代器返回的顺序相同。
  - **参数:**
    - `c` - 要放入此列表中的元素的集合
  - **抛出:**
    - `NullPointerException` - 如果指定的集合为null

## 方法

- **`void trimToSize()`**
  - 将此 `ArrayList` 实例的容量调整为列表的当前大小。

- **`void ensureCapacity(int minCapacity)`**
  - 如有必要，增加此 `ArrayList` 实例的容量，以确保其至少可以容纳由最小容量参数指定的元素数量。
  - **参数:**
    - `minCapacity` - 所需的最小容量

- **`int size()`**
  - 返回此列表中的元素数。

- **`boolean isEmpty()`**
  - 如果此列表不包含任何元素，则返回 `true`。

- **`boolean contains(Object o)`**
  - 如果此列表包含指定的元素，则返回 `true`。
  - **参数:**
    - `o` - 要测试其在此列表中存在性的元素

- **`int indexOf(Object o)`**
  - 返回此列表中指定元素的第一次出现的索引；如果此列表不包含该元素，则返回 -1。
  - **参数:**
    - `o` - 要搜索的元素

- **`int lastIndexOf(Object o)`**
  - 返回此列表中指定元素的最后一次出现的索引；如果此列表不包含该元素，则返回 -1。
  - **参数:**
    - `o` - 要搜索的元素

- **`Object clone()`**
  - 返回此 `ArrayList` 实例的浅拷贝。（元素本身不会被复制。）

- **`Object[] toArray()`**
  - 返回一个数组，其中包含此列表中所有元素的正确顺序。

- **`<T> T[] toArray(T[] a)`**
  - 返回一个数组，其中包含此列表中所有元素的正确顺序；返回数组的运行时类型是指定数组的类型。
  - **参数:**
    - `a` - 要存储列表元素的数组

- **`E get(int index)`**
  - 返回此列表中指定位置的元素。
  - **参数:**
    - `index` - 要返回的元素的索引

- **`E getFirst()`**
  - 获取此集合的第一个元素。

- **`E getLast()`**
  - 获取此集合的最后一个元素。

- **`E set(int index, E element)`**
  - 用指定元素替换此列表中指定位置的元素。
  - **参数:**
    - `index` - 要替换的元素的索引
    - `element` - 要存储在指定位置的元素

- **`boolean add(E e)`**
  - 将指定元素追加到此列表的末尾。

- **`void add(int index, E element)`**
  - 在此列表中指定位置插入指定元素。
  - **参数:**
    - `index` - 要插入指定元素的索引
    - `element` - 要插入的元素

- **`void addFirst(E element)`**
  - 将元素添加为此集合的第一个元素。

- **`void addLast(E element)`**
  - 将元素添加为此集合的最后一个元素。

- **`E remove(int index)`**
  - 删除此列表中指定位置的元素。
  - **参数:**
    - `index` - 要移除的元素的索引

- **`E removeFirst()`**
  - 删除并返回此集合的第一个元素。

- **`E removeLast()`**
  - 删除并返回此集合的最后一个元素。

- **`boolean equals(Object o)`**
  - 将指定对象与此列表进行比较以检查是否相等。

- **`int hashCode()`**
  - 返回此列表的哈希码值。

- **`boolean remove(Object o)`**
  - 从此列表中删除指定元素的第一个出现，如果存在的话。

- **`void clear()`**
  - 从此列表中删除所有元素。

- **`boolean addAll(Collection<? extends E> c)`**
  - 将指定集合中的所有元素追加到此列表的末尾。
  - **参数:**
    - `c` - 包含要添加到此列表中的元素的集合

- **`boolean addAll(int index, Collection<? extends E> c)`**
  - 将指定集合中的所有元素从指定位置开始插入到此列表中。
  - **参数:**
    - `index` - 要从指定集合中插入第一个元素的索引
    - `c` - 包含要添加到此列表中的元素的集合

- **`protected void removeRange(int fromIndex, int toIndex)`**
  - 从此列表中删除索引位于 `fromIndex`（包括）和 `toIndex`（不包括）之间的所有元素。
  - **参数:**
    - `fromIndex` - 要删除的第一个元素的索引
    - `toIndex` - 要删除的最后一个元素之后的索引

- **`boolean removeAll(Collection<?> c)`**
  - 从此列表中删除包含在指定集合中的所有元素。

- **`boolean retainAll(Collection<?> c)`**
  - 仅保留此列表中包含在指定集合中的元素。

- **`ListIterator<E> listIterator(int index)`**
  - 返回一个列表迭代器，从指定位置开始遍历此列表中的元素。
  - **参数:**
    - `index` - 要从列表迭代器返回的第一个元素的索引

- **`ListIterator<E> listIterator()`**
  - 返回一个列表迭代器，该迭代器按正确顺序遍历此列表中的元素。

- **`Iterator<E> iterator()`**
  - 返回一个迭代器，该迭代器按正确顺序遍历此列表中的元素。

- **`List<E> subList(int fromIndex, int toIndex)`**
  - 返回此列表中指定范围的视图。
  - **参数:**
    - `fromIndex` - 子列表的低端点（包括）
    - `toIndex` - 子列表的高端点（不包括）

- **`void forEach(Consumer<? super E> action)`**
  - 对 `Iterable` 的每个元素执行给定操作。

- **`Spliterator<E> spliterator()`**
  - 创建一个在此列表中的元素上进行延迟绑定和快速失败的 `Spliterator`。

- **`boolean removeIf(Predicate<? super E> filter)`**
  - 删除满足给定谓词的此集合的所有元素。
  - **参数:**
    - `filter` - 一个返回 `true` 以删除元素的谓词
