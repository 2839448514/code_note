现代 C++ 模板是一种强大的编程工具，它允许开发者编写泛型、灵活且高效的代码。模板是 C++ 泛型编程的核心，使得程序员可以编写独立于数据类型的代码。现代 C++（C++11 及以后）对模板进行了许多改进，使其更易用、更强大。以下是一些现代 C++ 模板的关键特性和概念：

### 1. **模板别名（Template Aliases）**

模板别名是 `typedef` 的现代化替代，它使用 `using` 关键字，可以更清晰地定义模板类型别名。

```cpp
template<typename T>
using Vec = std::vector<T>;
Vec<int> v;  // 等价于 std::vector<int> v;
```

### 2. **可变参数模板（Variadic Templates）**

可变参数模板允许一个模板接受任意数量的模板参数。它对于编写处理不同数量参数的函数或类非常有用。

```cpp
template<typename... Args>
void print(Args... args) {
    (std::cout << ... << args) << '\n'; // 折叠表达式 (C++17)
}
print(1, 2, "hello", 3.14); // 输出: 1 2 hello 3.14
```

### 3. **折叠表达式（Fold Expressions）**

折叠表达式用于处理可变参数模板中的参数包，可以轻松地进行递归计算或操作。

```cpp
template<typename... Args>
auto sum(Args... args) {
    return (args + ...);  // 左折叠： (((args1 + args2) + args3) + ...)
}
```

### 4. **类型特征（Type Traits）**

类型特征是用于查询或操作类型的工具，它们主要用于编译时类型检查和类型操作。

```cpp
template<typename T>
void func(T val) {
    if constexpr (std::is_integral_v<T>) {
        std::cout << val << " is an integral type\n";
    } else {
        std::cout << val << " is not an integral type\n";
    }
}
func(42);    // 输出: 42 is an integral type
func(3.14);  // 输出: 3.14 is not an integral type
```

### 5. **SFINAE 和 `std::enable_if`**

SFINAE（Substitution Failure Is Not An Error）是一种模板元编程技术，允许在编译时根据条件选择合适的函数或类模板实例化。

```cpp
template<typename T>
typename std::enable_if<std::is_integral<T>::value, T>::type
increment(T t) {
    return t + 1;
}

increment(1);  // 正常工作，返回 2
// increment(3.14); // 编译错误，因为 double 不是 integral 类型
```

### 6. **概念（Concepts）**

概念（Concepts）是 C++20 引入的新特性，用于限制模板参数的类型，类似于泛型编程中的约束机制。它使模板代码更加可读和易于调试。

```cpp
template<typename T>
concept Integral = std::is_integral_v<T>;

template<Integral T>
T add(T a, T b) {
    return a + b;
}

add(1, 2);    // 正常工作
// add(1.0, 2.0); // 编译错误，因为 double 不满足 Integral 概念
```

### 7. **编译时常量表达式（constexpr）**

`constexpr` 可以用于编写编译时计算的常量表达式，提高程序的性能。

```cpp
constexpr int factorial(int n) {
    return (n <= 1) ? 1 : (n * factorial(n - 1));
}
static_assert(factorial(5) == 120, "Error in factorial");
```

### 8. **模板的默认参数和模板的特化**

模板可以具有默认参数，也可以根据特定的类型进行特化（全特化和偏特化）。

```cpp
template<typename T = int>
class MyClass {
    // 默认使用 int 类型
};

template<>
class MyClass<double> {
    // 针对 double 类型的全特化
};
```

### 9. **模板元编程（Template Metaprogramming）**

模板元编程是一种编写可以在编译时执行计算的技术，它使用模板递归和类型推导来在编译时生成代码。这种技术用于实现复杂的逻辑，如编译时类型检查、选择等。

**示例：计算编译时的斐波那契数列**

```cpp
template<int N>
struct Fibonacci {
    static const int value = Fibonacci<N-1>::value + Fibonacci<N-2>::value;
};

template<>
struct Fibonacci<1> {
    static const int value = 1;
};

template<>
struct Fibonacci<0> {
    static const int value = 0;
};

// 使用：计算 Fibonacci<10>::value
int main() {
    int result = Fibonacci<10>::value; // result 为 55
}
```

### 10. **依赖类型名称（Dependent Name）**

在模板中，有些名称依赖于模板参数（称为依赖类型名称），需要使用 `typename` 或 `template` 关键字来明确指示编译器如何解析这些名称。

**示例：使用 `typename` 明确依赖类型名称**

```cpp
template<typename T>
class MyClass {
    typename T::SubType* ptr; // T::SubType 是一个依赖类型，需要使用 typename
};
```

**示例：使用 `template` 明确依赖模板**

```cpp
template<typename T>
class Wrapper {
public:
    template<typename U>
    void func(U u) { /*...*/ }
};

template<typename T>
void callFunc(Wrapper<T>& w) {
    w.template func<int>(5); // 需要使用 template 指示 func 是模板
}
```

### 11. **模板偏特化（Partial Specialization）**

模板偏特化允许为某些特定的类型或条件提供特殊的实现，而不是为所有类型提供通用实现。它比全特化更灵活，因为全特化要求所有参数都必须明确。

**示例：偏特化处理指针类型**

```cpp
template<typename T>
class MyClass {
public:
    void print() {
        std::cout << "General type" << std::endl;
    }
};

// 偏特化：处理指针类型
template<typename T>
class MyClass<T*> {
public:
    void print() {
        std::cout << "Pointer type" << std::endl;
    }
};
```

### 12. **模板递归（Template Recursion）**

模板递归是模板元编程的基础，通过递归地实例化模板，可以在编译时完成很多复杂的计算。

**示例：求编译时的阶乘**

```cpp
template<int N>
struct Factorial {
    static const int value = N * Factorial<N - 1>::value;
};

template<>
struct Factorial<0> {
    static const int value = 1;
};

// 使用：Factorial<5>::value 为 120
```

### 13. **CRTP（Curiously Recurring Template Pattern）**

CRTP 是一种使用模板实现静态多态性的设计模式。子类将自己作为模板参数传递给父类模板，以便父类可以在编译时了解子类的具体类型。

**示例：CRTP 实现静态多态性**

```cpp
template<typename Derived>
class Base {
public:
    void interface() {
        static_cast<Derived*>(this)->implementation();
    }
};

class Derived : public Base<Derived> {
public:
    void implementation() {
        std::cout << "Derived implementation" << std::endl;
    }
};

int main() {
    Derived d;
    d.interface(); // 输出: Derived implementation
}
```

### 14. **表达式模板（Expression Templates）**

表达式模板是一种技术，用于避免临时对象的创建，提高计算密集型代码（如数值计算）的性能。它将运算符重载与模板结合，以延迟计算表达式，避免中间结果的生成。

**示例：简单的表达式模板**

```cpp
template<typename T>
class Vector {
    T* data;
    size_t size;
public:
    Vector(size_t n) : size(n) { data = new T[n]; }
    ~Vector() { delete[] data; }

    T& operator[](size_t i) { return data[i]; }
    const T& operator[](size_t i) const { return data[i]; }

    // 重载加法运算符，使用表达式模板
    Vector operator+(const Vector& rhs) {
        Vector result(size);
        for (size_t i = 0; i < size; ++i)
            result[i] = data[i] + rhs[i];
        return result;
    }
};
```

### 15. **动态多态性与静态多态性的结合**

模板可以与虚函数结合使用，混合动态多态性和静态多态性，从而在保持类型安全的同时提高运行时性能。

**示例：虚函数与模板结合**

```cpp
class Base {
public:
    virtual void display() = 0; // 纯虚函数
};

template<typename T>
class Derived : public Base {
public:
    void display() override {
        std::cout << "Displaying Derived of type " << typeid(T).name() << std::endl;
    }
};
```

### 16. **模板参数推导指引（Template Argument Deduction Guides）**

C++17 引入了模板参数推导指引，可以自动推导类模板的模板参数，而无需显式指定类型。

**示例：模板参数推导**

```cpp
template<typename T>
class MyPair {
public:
    T first, second;
    MyPair(T a, T b) : first(a), second(b) {}
};

// 推导指引，允许在构造时自动推导类型
MyPair(const char*, const char*) -> MyPair<std::string>;

int main() {
    MyPair p("hello", "world"); // 自动推导为 MyPair<std::string>
}
```

### 17. **智能指针（Smart Pointers）和模板**

智能指针是现代 C++ 的重要组成部分，如 `std::unique_ptr` 和 `std::shared_ptr`。它们是利用模板实现的安全指针封装，提供了资源管理和异常安全性。

**示例：使用 `std::unique_ptr`**

```cpp
std::unique_ptr<int> ptr = std::make_unique<int>(10);
std::cout << *ptr << std::endl; // 输出 10
```

### 18. **元函数（Metafunctions）和 `std::conditional`**

元函数是一种用于在编译时生成类型或值的模板，它们通常与 `std::conditional` 和 `std::integral_constant` 等工具结合使用。

**示例：选择性类型定义**

```cpp
template<bool Condition, typename T, typename F>
using ConditionalType = typename std::conditional<Condition, T, F>::type;

ConditionalType<true, int, double> x; // x 为 int 类型
ConditionalType<false, int, double> y; // y 为 double 类型
```

### 19. **模板的递归继承（Template Recursive Inheritance）**

递归继承是一种常用于组合多个类型的模式，在元编程中很有用。它通常用于实现类似多态性的行为。

**示例：实现多类型的继承**

```cpp
template<typename... Mixins>
class Combined : public Mixins... {
public:
    void doSomething() {
        // 调用所有基类的成员函数
        (Mixins::doSomething(), ...);
    }
};

struct Mixin1 {
    void doSomething() { std::cout << "Mixin1\n"; }
};

struct Mixin2 {
    void doSomething() { std::cout << "Mixin2\n"; }
};

int main() {
    Combined<Mixin1, Mixin2> combined;
    combined.doSomething(); // 输出: Mixin1\nMixin2\n
}
```

### 20. **完美转发（Perfect Forwarding）**

完美转发是一种模板技术，可以将参数精确地传递给另一个函数或构造函数。它通常与 `std::forward` 和 `std::move` 结合使用。

**示例：完美转发构造函数参数**

```cpp
#include <utility>

template<typename T>
class Wrapper {
public:
    template<typename... Args>
    Wrapper(Args&&... args) : data_(std::forward<Args>(args)...) {}

private:
    T data_;
};

struct ComplexType {
    ComplexType(int x, double y) { std::cout << "ComplexType constructed\n"; }
};

int main() {
    Wrapper<ComplexType> wrapped(42, 3.14); // 完美转发到 ComplexType 构造函数
}
```

### 21. **Lambda 与模板结合（Generic Lambda and Template Lambdas）**

现代 C++ 中的 Lambda 表达式可以作为模板使用，从而更方便地编写泛型代码。

**示例：泛型 Lambda**

```cpp
auto add = [](auto a, auto b) { return a + b; };
std::cout << add(1, 2) << std::endl;      // 输出 3
std::cout << add(1.5, 2.5) << std::endl;  // 输出 4.0
```

**示例：捕获外部模板变量**

```cpp
template<typename T>
void callLambda(T lambda) {
    lambda();
}

int main() {
    int x = 42;
    auto lambda = [=]() { std::cout << x << std::endl; };
    callLambda(lambda); // 输出: 42
}
```

### 22. **模板的非类型参数（Non-Type Template Parameters）**

模板不仅可以接受类型参数，还可以接受常量、指针、引用等非类型参数。

**示例：非类型模板参数实现数组包装类**

```cpp
template<int N>
struct Array {
    int data[N];
    int size() const { return N; }
};

Array<10> arr; // 创建大小为 10 的数组
std::cout << arr.size() << std::endl; // 输出 10
```

### 23. **依赖于值的模板元编程（Value-Based Template Metaprogramming）**

这种技术用于编译时的常量推导、条件判断和静态断言等。

**示例：编译时判断奇偶性**

```cpp
template<int N>
struct IsEven {
    static const bool value = N % 2 == 0;
};

static_assert(IsEven<4>::value, "Number is not even"); // 编译时检查是否为偶数
```

### 24. **模板的元函数（Template Metafunctions）**

元函数是一种常见的模板元编程技术，通常用于实现编译时类型计算。

**示例：检测类型是否为指针**

```cpp
template<typename T>
struct IsPointer {
    static const bool value = false;
};

template<typename T>
struct IsPointer<T*> {
    static const bool value = true;
};

std::cout << IsPointer<int>::value << std::endl;   // 输出 0
std::cout << IsPointer<int*>::value << std::endl;  // 输出 1
```

### 25. **CRTP 与模板元编程结合（Combining CRTP with Metaprogramming）**

将 CRTP 和模板元编程结合可以实现更复杂的设计模式，例如静态接口、多层继承、编译时计算等。

**示例：CRTP 实现静态接口检查**

```cpp
template<typename Derived>
class InterfaceChecker {
public:
    void check() {
        static_cast<Derived*>(this)->implementation(); // 检查 Derived 类是否有 implementation 方法
    }
};

class Derived : public InterfaceChecker<Derived> {
public:
    void implementation() { std::cout << "Implementation provided.\n"; }
};

int main() {
    Derived d;
    d.check(); // 输出: Implementation provided.
}
```

### 26. **constexpr 与模板的组合使用**

`constexpr` 可以与模板结合使用，在编译时完成复杂的计算或判断。

**示例：编译时字符串哈希**

```cpp
constexpr unsigned int hash(const char* str, int h = 0) {
    return !str[h] ? 5381 : (hash(str, h+1) * 33) ^ str[h];
}

constexpr unsigned int hashed = hash("test");
static_assert(hashed == 2090756197, "Hash does not match!");
```

### 27. **概念（Concepts）的进阶应用**

C++20 的 Concepts 提供了一种更强大的方式来定义模板的约束，可以用于编写复杂的泛型库。

**示例：概念与类型推导结合**

```cpp
#include <concepts>

template<typename T>
concept Addable = requires(T a, T b) {
    { a + b } -> std::same_as<T>;
};

template<Addable T>
T add(T a, T b) {
    return a + b;
}

std::cout << add(1, 2) << std::endl;   // 输出 3
// std::cout << add("Hello, ", "World!"); // 编译错误，不满足 Addable 概念
```

### 28. **模板的递归包展开（Recursive Pack Expansion with Templates）**

可变参数模板包的递归展开是一种用于处理复杂数据结构的技巧。

**示例：递归展开参数包**

```cpp
template<typename... Args>
void print(Args... args) {
    (std::cout << ... << args) << '\n'; // 使用 fold 表达式展开参数包
}

print(1, 2, 3, "hello", 4.5); // 输出: 1 2 3 hello 4.5
```

### 29. **模板的默认特化（Default Template Specialization）**

默认特化允许我们为模板提供一个通用的默认实现，并在特定情况下重载特化。

**示例：为指针类型提供默认特化**

```cpp
template<typename T>
struct RemovePointer {
    using Type = T;
};

template<typename T>
struct RemovePointer<T*> {
    using Type = T;
};

// RemovePointer<int*>::Type => int
```

### 30. **混合策略模式（Mix-in Policy Pattern）**

模板的多继承和特化可以用于实现类似策略模式的设计，使得代码更灵活。

**示例：策略模式的多重继承实现**

```cpp
template<typename Policy>
class Base : public Policy {
public:
    void interface() {
        this->policyMethod(); // 调用策略方法
    }
};

class ConcretePolicy {
public:
    void policyMethod() {
        std::cout << "ConcretePolicy Method" << std::endl;
    }
};

Base<ConcretePolicy> obj;
obj.interface(); // 输出: ConcretePolicy Method
```