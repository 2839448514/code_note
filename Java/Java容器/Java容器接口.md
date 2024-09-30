---
tags:
  - Java
---
# Java容器接口

| **接口/类**                   | **描述**                                                                             | **特性**                                                                                 | **常见实现**                                           |
| -------------------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------- |
| **BeanContext**            | `BeanContext` 是一个 JavaBeans 组件的容器接口，允许多个 JavaBeans 组件在同一个上下文中协作和通信。它可以管理组件之间的依赖关系。 | - 继承 `Collection` 接口。<br> - 管理多个 JavaBeans 组件。<br> - 支持嵌套的组件结构。<br> - 管理组件的生命周期。       | - `BeanContextSupport`                             |
| **BeanContextServices**    | `BeanContextServices` 是 `BeanContext` 的扩展，允许 JavaBeans 组件通过上下文查找和注册服务。             | - 提供服务的注册和获取。<br> - 支持服务使用的撤销和管理。                                                      | - `BeanContextServicesSupport`                     |
| **BlockingDeque<E>**       | `BlockingDeque` 是一个双端阻塞队列，支持在队列两端插入和移除元素，并允许线程阻塞等待队列操作。                            | - 支持线程安全操作。<br> - 当队列为空或满时，插入和删除操作会阻塞。<br> - 提供阻塞的获取和放置方法，如 `putFirst()`、`takeLast()`。 | - `LinkedBlockingDeque`                            |
| **BlockingQueue<E>**       | `BlockingQueue` 是一个支持阻塞操作的队列接口，通常用于多线程环境下的任务调度或数据传输。                               | - 支持线程安全操作。<br> - 当队列为空时，获取操作会阻塞，直到有元素可用。<br> - 当队列已满时，插入操作会阻塞，直到有空间。                  | - `ArrayBlockingQueue`<br> - `LinkedBlockingQueue` |
| **Deque<E>**               | `Deque` 是双端队列接口，允许在队列的两端插入和删除元素。可以用作栈（LIFO）或队列（FIFO）。                              | - 支持两端的插入和删除。<br> - 既可以作为栈，也可以作为队列。<br> - 支持 `addFirst()`、`removeLast()` 等操作。          | - `LinkedList`<br> - `ArrayDeque`                  |
| **EventSet**               | `EventSet` 是 JavaBeans 组件模型中的接口，用于管理一组事件及其监听器。                                     | - 管理多个事件源与监听器的交互。<br> - 允许注册和移除事件监听器。                                                  | - `EventSetDescriptor`                             |
| **List<E>**                | `List` 是一个有序集合接口，支持按插入顺序存储元素，允许重复元素。                                               | - 支持按索引访问元素。<br> - 允许元素重复。<br> - 提供基本的集合操作，如添加、删除、修改、遍历。                               | - `ArrayList`<br> - `LinkedList`                   |
| **NavigableSet<E>**        | `NavigableSet` 是 `SortedSet` 的子接口，提供对有序集合的导航操作，允许查找比给定元素大或小的最近元素。                  | - 支持自动排序。<br> - 提供 `floor()`、`ceiling()` 等方法查找最近元素。<br> - 支持从有序集合中获取子集。                | - `TreeSet`                                        |
| **Queue<E>**               | `Queue` 是一个队列接口，通常用于先进先出 (FIFO) 顺序处理。                                              | - 提供 `offer()`、`poll()`、`peek()` 等队列操作。<br> - 通常遵循 FIFO，但某些实现（如优先队列）可能使用不同的顺序规则。       | - `LinkedList`<br> - `PriorityQueue`               |
| **SequencedCollection<E>** | `SequencedCollection` 是一个有序集合接口，支持从头到尾和从尾到头的遍历。                                    | - 提供双向迭代器。<br> - 保证集合中的元素有序。                                                           | - 尚未有官方标准实现，通常作为自定义实现。                             |
| **SequencedSet<E>**        | `SequencedSet` 是 `Set` 的子接口，表示有序且唯一的集合，支持从头到尾和从尾到头的遍历。                             | - 保证元素唯一性。<br> - 元素按插入顺序存储。<br> - 支持正向和反向遍历。                                           | - 尚未有官方标准实现，通常作为自定义实现。                             |
| **Set<E>**                 | `Set` 是一个不允许重复元素的集合接口，通常无序。                                                        | - 保证集合中没有重复元素。<br> - 通常不保证元素顺序。                                                        | - `HashSet`<br> - `LinkedHashSet`<br> - `TreeSet`  |
| **SortedSet<E>**           | `SortedSet` 是 `Set` 的子接口，表示按自然顺序或自定义比较器排序的集合。                                      | - 保证元素按升序排列。<br> - 提供方法获取子集、首尾元素等。                                                     | - `TreeSet`                                        |
| **TransferQueue<E>**       | `TransferQueue` 是 `BlockingQueue` 的扩展，允许生产者线程阻塞直到消费者接收到元素。                         | - 生产者可以直接将元素传递给消费者。<br> - 支持传统队列的插入和移除操作。                                              | - `LinkedTransferQueue`                            |

### 详细描述：

1. **BeanContext 和 BeanContextServices**：这两个接口用于 JavaBeans 组件的管理，提供了一种通过上下文协调多个组件的方法。其中 `BeanContextServices` 增加了服务查找和注册功能，允许组件之间共享服务。

2. **BlockingDeque 和 BlockingQueue**：这两个接口是阻塞队列，主要用于多线程环境。`BlockingDeque` 是双端队列，支持两端插入和移除元素，而 `BlockingQueue` 是单端队列，通常用作任务队列。阻塞特性确保队列满或空时操作会阻塞直到状态改变。

3. **Deque 和 Queue**：`Deque` 和 `Queue` 都是队列接口，`Deque` 支持双端操作（可用作栈或队列），而 `Queue` 是单端操作的队列，通常用于先进先出 (FIFO) 场景。

4. **List**：`List` 接口表示一个有序集合，支持通过索引访问元素，并允许重复元素。`ArrayList` 和 `LinkedList` 是它的常见实现，分别使用动态数组和链表作为底层数据结构。

5. **NavigableSet 和 SortedSet**：这两个接口用于有序集合。`SortedSet` 仅提供元素的排序功能，而 `NavigableSet` 进一步支持导航操作，如查找最近的比给定元素大或小的元素。

6. **SequencedCollection 和 SequencedSet**：这些接口表示有序集合，除了支持元素顺序访问外，还支持正向和反向遍历，但目前没有官方的标准实现。

7. **Set**：`Set` 是一个集合接口，保证集合中的元素是唯一的。`HashSet` 是基于哈希表的无序集合，而 `TreeSet` 是基于红黑树的有序集合。

8. **TransferQueue**：这是 `BlockingQueue` 的扩展，允许生产者直接将元素传递给消费者，适合高并发场景下的任务调度。
