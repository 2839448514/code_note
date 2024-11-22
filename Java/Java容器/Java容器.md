---
tags:
  - Java
---
# Java容器



|分类|列表 (List)|集合 (Set)|映射 (Map)|队列 (Queue)|
|---|---|---|---|---|
|**接口**|`List`<br>_(无法实例化)_|`Set`<br>_(无法实例化)_|`Map`<br>_(无法实例化)_|`Queue`<br>_(无法实例化)_|
|**基本实现**|`ArrayList`|`HashSet`|`HashMap`|`LinkedList` (作为队列)|
|**线程安全**|`CopyOnWriteArrayList`|`CopyOnWriteArraySet`|`ConcurrentHashMap`|`PriorityBlockingQueue`|
|**同步封装**|`Collections.synchronizedList()`|`Collections.synchronizedSet()`|`Collections.synchronizedMap()`|`Collections.synchronizedQueue()`|
|**不可修改**|`Collections.unmodifiableList()`|`Collections.unmodifiableSet()`|`Collections.unmodifiableMap()`|`Collections.unmodifiableQueue()`|
|**特殊实现**|`LinkedList`|`TreeSet`|`TreeMap`|`PriorityQueue`|
|**其他**|`Vector` (旧式同步列表)|`LinkedHashSet`|`WeakHashMap`|`ArrayDeque` (双端队列)|

这个表格提供了一个概览，展示了Java中不同类型的容器以及它们的一些常见实现。需要注意的是，每个容器都有其特定的应用场景和性能特征，例如`ArrayList`提供了快速的随机访问，而`LinkedList`则更适合于频繁的插入和删除操作。

- `List` 接口表示一个有序的集合，允许元素重复。
- `Set` 接口表示一个不包含重复元素的集合。
- `Map` 接口存储键值对，并且不允许键重复。
- `Queue` 接口通常遵循先进先出（FIFO）原则，但也有像`PriorityQueue`这样的变种，它根据元素的优先级来排序。


## Java容器详细图解

![[1.png]]

## Java容器简易图解

![[2.png]]

---


![[Interface IterableT.png]]