---
tags:
  - CPP
---

# `cv（const 与 volatile）`类型限定符

可出现于任何类型说明符（包括[[声明]]的 声明说明符序列）中，以指定被声明对象或被命名类型的常量性（constness）或易变性（volatility）。

- `**const**` ——定义类型为_常量_。
- `**volatile**` ——定义类型为_易变_。
---

### 解释

对于除了[[函数|函数类型]]或[[引用声明|引用类型]]以外的任何类型 `T`（包括不完整类型），C++ 类型系统中有另外三个独立的类型：==**`const`-限定的 `T`**==、==**`volatile`-限定的 `T`**== 及 ==**`const-volatile`-限定的 `T`**==。

**注意**：**[[数组声明|数组类型]]被当做与其元素类型有相同的 `cv` 限定**。

当对象最初被创建时，所用的 `cv` 限定符（可以是[[声明]]中的 声明说明符序列 或 声明符 的一部分，或者是 [[new 表达式]]中的 类型标识 的一部分）决定对象的常量性或易变性，如下所示：

- _**`const` 对象**_——**类型为 `const`-限定的 对象，或 `const` 对象的非 `mutable` 子对象**。这种对象不能修改：尝试直接这么做是编译时错误，而尝试间接这么做（例如通过到非 `const` 类型的引用或指针修改 `const` 对象）导致未定义行为。
- _**`volatile` 对象**_——类型为 `volatile`-限定的 对象，或 `volatile` 对象的子对象，或 `const volatile` 对象的 `mutable` 子对象。通过 `volatile` 限定的类型的泛左值表达式的每次访问（读或写操作、成员函数调用等），都被当作对于[[如同规则|优化]]而言是可见的副作用（即在单个执行线程内，`volatile` 访问不能被优化掉，或者与另一[[求值顺序|按顺序早于]]或按顺序晚于该 `volatile` 访问的可见副作用进行重排序。这使得 `volatile` 对象适用于与[信号处理函数](https://www.apiref.com/cpp-zh/cpp/utility/program/signal.html "cpp/utility/program/signal")之间的交流，但不适于与另一执行线程交流，参阅 [std::memory_order](https://www.apiref.com/cpp-zh/cpp/atomic/memory_order.html "cpp/atomic/memory order")）。试图通过非 `volatile` [[值类别#泛左值（glvalue）|泛左值]]涉指 volatile 对象（例如，通过到非 `volatile` 类型的引用或指针）会导致未定义行为。
- _**`const volatile 对象`**_——类型为 `const-volatile`-限定的 对象，`const volatile` 对象的非 `mutable` 子对象，`volatile` 对象的 `const` 子对象，或 `const` 对象的非 `mutable volatile` 子对象。同时表现为 `const` 对象与 `volatile` 对象。
---

### mutable 说明符

**`mutable` 修饰符是用来表示类的非静态成员在常量成员函数中可以被修改的。**

- **`mutable`** - **容许在即便包含它的对象被声明为 const 时仍可修改声明为 mutable 的类成员。**

可出现于非引用非 const 类型的[[非静态数据成员]]的声明中：

```c++
class X {
  mutable const int* p;         // OK
  mutable int* const q;         // 非良构
};
```

> [!NOTE] **良构和非良构**
>  **良构**（Well-formed）：一个程序被称为“良构”，意味着它符合 C++ 语言的语法和语义规则，可以被编译器正确地理解和编译。
> **非良构**（Ill-formed）：一个程序被称为“非良构”，意味着它违反了语言的某些规则，因此无法被正确编译。

---

- **修饰成员变量**：当你在类定义中使用 `mutable` 修饰一个数据成员时，这个成员可以在 `const` 成员函数中被修改。例如：

```c++
class Example {
public:
    mutable int counter;

    Example() : counter(0) {}

    void increment() const {
        counter++; // 在 const 成员函数中修改 mutable 成员
    }
};
```

- **常量对象的修改**：通常，`const` 对象中的成员变量不能被修改，但如果某个成员被声明为 `mutable`，那么即使在 `const` 对象的上下文中也可以修改它。

****

**`mutable` 用于指定不影响类的外部可观察状态的成员**（通常用于互斥体、记忆缓存、惰性求值和访问指令等）。

```c++
class ThreadsafeCounter {
  mutable std::mutex m; // “M&M 规则”：mutable 与 mutex 一并出场
  int data = 0;
 public:
  int get() const {
    std::lock_guard<std::mutex> lk(m);
    return data;
  }
  void inc() {
    std::lock_guard<std::mutex> lk(m);
    ++data;
  }
};
```

### 转换

> [!NOTE] **基于限制性的增长顺序的 `cv` 限定符的偏序**
> 基于限制性的增长顺序的 `cv` 限定符的偏序是指对类型的 `const` 和 `volatile` 限定符的组合进行排序的一种方法。具体来说，这种偏序关系定义了不同的 `cv` 限定符组合之间的层次关系。

**存在一种基于限制性的增长顺序的 `cv` 限定符的偏序**。从而可以称类型具有_更多_或_更少_的 `cv` 限定：

- _无限定_ < `const`
- _无限定_ < `volatile`
- _无限定_ < `const volatile`
- `const` < `const volatile`
- `volatile` < `const volatile`

到 `cv` 限定类型的引用和指针能被[[隐式转换]]到_更多 cv 限定_的类型的引用和指针。特别是允许下列转换：

- 到_非限定_类型的引用/指针能被转换成到 `const` 的引用/指针
- 到_非限定_类型的引用/指针能被转换成到 `volatile` 的引用/指针
- 到_非限定_类型的引用/指针能被转换成到 `const volatile` 的引用/指针
- 到 `const` 类型的引用/指针能被转换成到 `const volatile` 的引用/指针
- 到 `volatile` 类型的引用/指针能被转换成到 `const volatile` 的引用/指针

注意：多级指针另有[[隐式转换|其他限制]]

欲将到 `cv` 限定类型的引用或指针转换为到_更少 `cv` 限定_类型的引用或指针，必须使用 [[const_cast 转换|const_cast]]。
