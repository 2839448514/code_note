---
tags:
  - Java
---
# Collection接口

## `Interface Collection<E>`

 **`public interface Collection<E> extends Iterable<E>`**

* 类型参数:

  `E` - 此集合中元素的类型

* 所有超级接口:

  `Iterable<E>`

* 所有已知子接口:

  `BeanContext`, `BeanContextServices`, `BlockingDeque<E>`, `BlockingQueue<E>`, `Deque<E>`, `EventSet`, `List<E>`, `NavigableSet<E>`, `Queue<E>`, `SequencedCollection<E>`, `SequencedSet<E>`, `Set<E>`, `SortedSet<E>`, `TransferQueue<E>`

* 所有已知实现类:

  `AbstractCollection`, `AbstractList`, `AbstractQueue`, `AbstractSequentialList`, `AbstractSet`, `ArrayBlockingQueue`, `ArrayDeque`, `ArrayList`, `AttributeList`, `BeanContextServicesSupport`, `BeanContextSupport`, `ConcurrentHashMap.KeySetView`, `ConcurrentLinkedDeque`, `ConcurrentLinkedQueue`, `ConcurrentSkipListSet`, `CopyOnWriteArrayList`, `CopyOnWriteArraySet`, `DelayQueue`, `EnumSet`, `HashSet`, `JobStateReasons`, `LinkedBlockingDeque`, `LinkedBlockingQueue`, `LinkedHashSet`, `LinkedList`, `LinkedTransferQueue`, `PriorityBlockingQueue`, `PriorityQueue`, `RoleList`, `RoleUnresolvedList`, `Stack`, `SynchronousQueue`, `TreeSet`, `Vector`

***

| 修饰符和类型                            | 方法                                             | 描述                                                                        |
|-----------------------------------------|--------------------------------------------------|------------------------------------------------------------------------------|
| `boolean`                               | `add(E e)`                                      | 确保此集合包含指定的元素（可选操作）。                                       |
| `boolean`                               | `addAll(Collection<? extends E> c)`            | 将指定集合中的所有元素添加到此集合中（可选操作）。                           |
| `void`                                  | `clear()`                                       | 从此集合中移除所有元素（可选操作）。                                       |
| `boolean`                               | `contains(Object o)`                            | 如果此集合包含指定的元素，则返回true。                                     |
| `boolean`                               | `containsAll(Collection<?> c)`                  | 如果此集合包含指定集合中的所有元素，则返回true。                           |
| `boolean`                               | `equals(Object o)`                             | 将指定对象与此集合进行比较以判断是否相等。                                 |
| `int`                                   | `hashCode()`                                    | 返回此集合的哈希码值。                                                     |
| `boolean`                               | `isEmpty()`                                     | 如果此集合不包含任何元素，则返回true。                                     |
| `Iterator<E>`                           | `iterator()`                                    | 返回此集合中元素的迭代器。                                                 |
| `default Stream<E>`                    | `parallelStream()`                              | 返回一个可能并行的Stream，其源为此集合。                                   |
| `boolean`                               | `remove(Object o)`                             | 从此集合中移除指定元素的单个实例（如果存在）（可选操作）。                  |
| `boolean`                               | `removeAll(Collection<?> c)`                    | 从此集合中移除也包含在指定集合中的所有元素（可选操作）。                    |
| `default boolean`                       | `removeIf(Predicate<? super E> filter)`       | 移除此集合中满足给定谓词的所有元素。                                       |
| `boolean`                               | `retainAll(Collection<?> c)`                    | 仅保留此集合中包含在指定集合中的元素（可选操作）。                         |
| `int`                                   | `size()`                                        | 返回此集合中的元素数量。                                                   |
| `default Spliterator<E>`               | `spliterator()`                                 | 在此集合中的元素上创建一个Spliterator。                                   |
| `default Stream<E>`                    | `stream()`                                      | 返回一个顺序Stream，其源为此集合。                                         |
| `Object[]`                              | `toArray()`                                     | 返回一个包含此集合中所有元素的数组。                                       |
| `default <T> T[]`                      | `toArray(IntFunction<T[]> generator)`         | 返回一个包含此集合中所有元素的数组，使用提供的generator函数来分配返回的数组。|
| `<T> T[]`                              | `toArray(T[] a)`                               | 返回一个包含此集合中所有元素的数组；返回的数组的运行时类型是指定数组的类型。|

---

### 方法介绍

1. **`int size()`**
   * **描述**：返回集合中元素的数量。如果集合中包含的元素超过 `Integer.MAX_VALUE`，则返回 `Integer.MAX_VALUE`。

2. **`boolean isEmpty()`**
   * **描述**：检查集合是否为空。如果集合不包含任何元素，则返回 `true`。

3. **`boolean contains(Object o)`**
   * **描述**：检查集合是否包含指定元素。如果集合中至少存在一个元素 `e` 使得 `Objects.equals(o, e)` 为 `true`，则返回 `true`。
   * **参数**：`o` - 要测试的元素。
   * **抛出**：`ClassCastException`（如果元素类型不兼容），`NullPointerException`（如果元素为 `null` 且集合不允许 `null` 元素）。

4. **`Iterator<E> iterator()`**
   * **描述**：返回集合中元素的迭代器。元素的返回顺序没有任何保证，除非该集合是某个提供保证的类的实例。

5. **`Object[] toArray()`**
   * **描述**：返回一个包含集合中所有元素的数组。如果集合的迭代器对元素的顺序有保证，此方法也必须以相同的顺序返回元素。

6. **`<T> T[] toArray(T[] a)`**
   * **描述**：返回一个包含集合中所有元素的数组，返回数组的运行时类型与指定数组相同。如果集合适合于指定数组，则返回该数组；否则，分配一个新数组。

7. **`default <T> T[] toArray(IntFunction<T[]> generator)`**
   * **描述**：使用提供的生成器函数分配返回的数组，返回包含集合中所有元素的数组。

8. **`boolean add(E e)`**
   * **描述**：确保集合包含指定元素。如果调用导致集合更改，则返回 `true`。如果集合不允许重复并且已包含该元素，则返回 `false`。

9. **`boolean remove(Object o)`**
   * **描述**：从集合中删除指定元素的单个实例。如果集合包含指定元素，则返回 `true`。

10. **`boolean containsAll(Collection<?> c)`**
    * **描述**：检查集合是否包含指定集合中的所有元素。

11. **`boolean addAll(Collection<? extends E> c)`**
    * **描述**：将指定集合中的所有元素添加到当前集合中。如果调用导致集合发生更改，则返回 `true`。

12. **`boolean removeAll(Collection<?> c)`**
    * **描述**：从集合中删除指定集合中包含的所有元素。调用后，集合将不再包含与指定集合中的元素相同的任何元素。

13. **`default boolean removeIf(Predicate<? super E> filter)`**
    * **描述**：删除集合中满足给定条件的所有元素。

14. **`boolean retainAll(Collection<?> c)`**
    * **描述**：仅保留集合中包含在指定集合中的元素。换句话说，从集合中删除不在指定集合中的所有元素。

15. **`void clear()`**
    * **描述**：从集合中删除所有元素。调用后，集合将为空。

16. **`boolean equals(Object o)`**
    * **描述**：将指定对象与集合进行比较以确定它们是否相等。

17. **`int hashCode()`**
    * **描述**：返回集合的哈希码值。

18. **`default Spliterator<E> spliterator()`**
    * **描述**：创建一个用于遍历集合中元素的 Spliterator。

19. **`default Stream<E> stream()`**
    * **描述**：返回一个以此集合为源的顺序 Stream。

20. **`default Stream<E> parallelStream()`**
    * **描述**：返回一个可能并行的以此集合为源的 Stream。

---
