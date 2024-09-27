在Java中，`print`、`printf`和`println`是用于输出文本到控制台的常用方法，它们都属于`PrintStream`类。尽管它们在功能上有些相似之处，但它们之间也存在一些关键的差异：

1. **`print` 方法**：
   - 该方法用于输出数据，但不会添加任何额外的字符（如换行符）。
   - 它只输出数据本身。
   - 例如：`System.out.print("Hello");` 会输出 "Hello" 但不换行。

2. **`println` 方法**：
   - 该方法用于输出数据，并在输出结束后自动添加一个换行符。
   - 它常用于输出数据后需要换行的场景。
   - 例如：`System.out.println("Hello");` 会输出 "Hello" 并换行。

3. **`printf` 方法**：
   - 该方法类似于C语言中的`printf`，它允许你格式化输出数据。
   - 你可以使用格式化字符串来控制输出的格式，比如数字的宽度、小数点后的位数等。
   - 它在输出结束后不会自动添加换行符。
   - 例如：`System.out.printf("%d %s\n", 123, "Hello");` 会输出 "123 Hello" 并换行。

### 具体示例：

- 使用 `print`：

  ```java
  System.out.print("Hello");
  System.out.print(" World");
  ```

  输出：`Hello World`（没有换行）

- 使用 `println`：

  ```java
  System.out.println("Hello");
  System.out.println("World");
  ```

  输出：

  ```c++
  Hello
  World
  ```

- 使用 `printf`：

  ```java
  System.out.printf("Hello %s\n", "World");
  System.out.printf("Number: %d\n", 123);
  ```

  输出：

  ```c++
  Hello World
  Number: 123
  ```
