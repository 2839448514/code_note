## `Interface Iterator<E>`

**`public interface Iterator<E>`**

#### 类型参数

- **E**: 迭代器返回的元素类型。

#### 已知的子接口

- **`EventIterator`**
- **`ListIterator<E>`**
- **`PrimitiveIterator<T, T_CONS>`**
- **`PrimitiveIterator.OfDouble`**
- **`PrimitiveIterator.OfInt`**
- **`PrimitiveIterator.OfLong`**
- **`XMLEventReader`**

#### 已知的实现类

- **`BeanContextSupport.BCSIterator`**
- **`EventReaderDelegate`**
- **`Scanner`**

---

| 修饰符和类型                          | 方法                                          | 描述                                                                                          |
|--------------------------------------|---------------------------------------------|-----------------------------------------------------------------------------------------------|
| `default void`                       | `forEachRemaining(Consumer<? super E> action)` | 对剩余的每个元素执行给定的操作，直到所有元素都已处理或操作引发异常。                          |
| `boolean`                            | `hasNext()`                                 | 如果迭代还有更多元素，则返回 `true`。                                                        |
| `E`                                  | `next()`                                    | 返回迭代中的下一个元素。                                                                      |
| `default void`                       | `remove()`                                  | 从底层集合中删除此迭代器返回的最后一个元素（可选操作）。                                      |

---

### `Iterator<E>` 接口方法介绍

#### 1. `boolean hasNext()`

- **描述**：检查迭代器是否还有更多元素。
  - 换句话说，如果 `next()` 方法将返回一个元素而不是引发异常，则返回 `true`。
- **返回**：如果迭代还有更多元素，则返回 `true`；否则返回 `false`。

#### 2. `E next()`

- **描述**：返回迭代中的下一个元素。
- **返回**：迭代中的下一个元素。
- **抛出**：
  - `NoSuchElementException`：如果迭代没有更多元素。

#### 3. `default void remove()`

- **描述**：从底层集合中删除此迭代器返回的最后一个元素（可选操作）。
  - 每次调用 `next()` 仅能调用此方法一次。
  - 如果在迭代过程中以除调用此方法外的任何方式修改底层集合，则迭代器的行为是未指定的，除非覆盖类已指定并发修改策略。
  - 如果在调用 `forEachRemaining()` 方法后调用此方法，则迭代器的行为是未指定的。
- **实现要求**：默认实现会抛出 `UnsupportedOperationException` 的实例，并不执行其他操作。
- **抛出**：
  - `UnsupportedOperationException`：如果此迭代器不支持 `remove` 操作。
  - `IllegalStateException`：如果尚未调用 `next()` 方法，或者在最后一次调用 `next()` 方法后已经调用 `remove()` 方法。

#### 4. `default void forEachRemaining(Consumer<? super E> action)`

- **描述**：对剩余的每个元素执行给定的操作，直到所有元素都已处理或操作引发异常。
  - 如果指定了顺序，则按迭代顺序执行操作。操作引发的异常将传递给调用者。
  - 如果操作以任何方式修改集合（甚至通过调用 `remove()` 方法或其他 `Iterator` 子类型的修改器方法），则迭代器的行为是未指定的，除非覆盖类已指定并发修改策略。
  - 如果操作引发异常，则迭代器的后续行为是未指定的。
- **实现要求**：默认实现的行为如下：

  ```java
  while (hasNext())
      action.accept(next());
  ```

- **参数**：
  - `action`：要对每个元素执行的操作。
- **抛出**：
  - `NullPointerException`：如果指定的操作为 `null`。
