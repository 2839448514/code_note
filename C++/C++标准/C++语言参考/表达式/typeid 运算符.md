---
tags:
  - CPP
---

# typeid 运算符

查询类型的信息。

用于必须知晓[[对象|多态对象]]的[[类型|动态类型]]的场合以及静态类型鉴别。

### 语法

- `typeid ( 类型 )`
- `typeid ( 表达式 )`

必须在使用 `typeid` 前包含头文件 `<typeinfo>`（若不包含该头文件，则每次使用关键词 `typeid` 都令程序为谬构。）

`typeid` 表达式为[[值类别|左值表达式]]，指代一个具有[[ static 成员|静态存储期]]的，多态类型 [std::type_info] 或某个其派生类型的 `const` 限定版本类型的对象。

### 解释

1) 指代一个表示 类型 类型的 [std::type_info] 对象。若 类型 为引用类型，则结果所指代的 [std::type_info] 对象表示被引用的类型。

2) 检验表达式 表达式

a) **若 表达式 为标识某个[[对象|多态类型]]（即声明或继承至少一个[[virtual 函数说明符|虚函数]]的类）对象的[[值类别|泛左值表达式]]，则 `typeid` 表达式对该表达式求值，然后指代表示该表达式动态类型的 [std::type_info]对象**。若该泛左值表达式为通过对一个指针应用一元 `*` 运算符所得，且该指针为空指针值，则抛出 [std::bad_typeid] 类型或从 [std::bad_typeid] 派生的类型的异常。

b) **若 表达式 不是多态类型的泛左值表达式，则 `typeid` [[表达式|不对该表达式求值]]，而它所指代的 [std::type_info] 对象表示该表达式的静态类型**。不进行左值到右值、数组到指针或函数到指针转换。然而对于纯右值参数，（形式上）要进行[[隐式转换|临时量实质化]]：参数必须在 `typeid` 表达式所出现的语境中可析构。 (C++17 起)

**在所有情况下，`typeid` 都忽略顶层的 `cv` 限定符（即 `typeid(T) == typeid(const T)`）。**

**若 `typeid` 的操作数为类类型或到类类型的引用，则该类类型必须不是[[类型|不完整类型]]。**

若对处于构造和销毁过程中的对象（在构造函数或析构函数之内，包括构造函数的[[构造函数与成员初始化器列表|初始化器列表]]或[[非静态数据成员|默认成员初始化器]]）使用 `typeid`，则此 `typeid` 所指代的 [std::type_info] 对象表示正在构造或销毁的类，即便它不是最终派生类。**

```c++
struct Foo;
struct S
{
   static int a[]; // 声明，不完整类型
   static Foo x;   // 声明，不完整类型
   static S s;     // 声明，不完整类型（在其自身定义中）
};
int S::a[10]; // 定义，完整类型
struct Foo {};
Foo S::x;     // 定义，完整类型
S S::s;       // 定义，完整类型
```

**然而，若声明使用了 [[constexpr 说明符(C++11 起)|constexpr]] 或[[inline 说明符|inline]] (C++17 起) 说明符，则必须声明该成员为具有完整类型。**(C++11 起)
### 注解

当应用于多态类型的表达式时，`typeid` 表达式的求值可能涉及运行时开销（虚表查找），其他情况下 `typeid` 表达式都在编译时解决。

`typeid` 所指代的对象的析构函数是否在程序结束时执行是未指明的。

不保证同一类型上的 typeid 表达式的所有求值都指代同一个 [std::type_info] 实例，不过这些 `type_info` 对象的 [std::type_info::hash_code] 相同，其 [std::type_index] 也相同。

```c++
const std::type_info& ti1 = typeid(A);
const std::type_info& ti2 = typeid(A);
 
assert(&ti1 == &ti2); // 不保证
assert(ti1.hash_code() == ti2.hash_code()); // 保证
assert(std::type_index(ti1) == std::type_index(ti2)); // 保证
```

## 示例
```C++
#include <iostream>
#include <string>
#include <typeinfo>
 
struct Base {}; // 非多态
struct Derived : Base {};
 
struct Base2 { virtual void foo() {} }; // 多态
struct Derived2 : Base2 {};
 
int main() {
    int myint = 50;
    [std::string](https://www.apiref.com/cpp-zh/cpp/string/basic_string.html) mystr = "string";
    double *mydoubleptr = nullptr;
 
    [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << "myint has type: " << typeid(myint).name() << '\n'
              << "mystr has type: " << typeid(mystr).name() << '\n'
              << "mydoubleptr has type: " << typeid(mydoubleptr).name() << '\n';
 
    // std::cout << myint 为多态类型的泛左值表达式；求值
    const [std::type_info](https://www.apiref.com/cpp-zh/cpp/types/type_info.html)& r1 = typeid([std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << myint);
    [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << '\n' << "std::cout<<myint has type : " << r1.name() << '\n';
 
    // std::printf() 不是多态类型的泛左值表达式；不求值
    const [std::type_info](https://www.apiref.com/cpp-zh/cpp/types/type_info.html)& r2 = typeid([std::printf](https://www.apiref.com/cpp-zh/cpp/io/c/fprintf.html)("%d\n", myint));
    [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << "printf(\"%d\\n\",myint) has type : " << r2.name() << '\n';
 
    // 非多态左值时为静态类型
    Derived d1;
    Base& b1 = d1;
    [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << "reference to non-polymorphic base: " << typeid(b1).name() << '\n';
 
    Derived2 d2;
    Base2& b2 = d2;
    [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << "reference to polymorphic base: " << typeid(b2).name() << '\n';
 
    try {
        // 解引用空指针：对于非多态表达式 OK
        [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << "mydoubleptr points to " << typeid(*mydoubleptr).name() << '\n'; 
        // 解引用空指针：对多态左值则不行
        Derived2* bad_ptr = nullptr;
        [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << "bad_ptr points to... ";
        [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << typeid(*bad_ptr).name() << '\n';
    } catch (const [std::bad_typeid](https://www.apiref.com/cpp-zh/cpp/types/bad_typeid.html)& e) {
         [std::cout](https://www.apiref.com/cpp-zh/cpp/io/cout.html) << " caught " << e.what() << '\n';
    }
}
```

输出
```c++
myint has type: int
mystr has type: std::basic_string<char, std::char_traits<char>, std::allocator<char> >
mydoubleptr has type: double*
50
std::cout<<myint has type : std::basic_ostream<char, std::char_traits<char> >
printf("%d\n",myint) has type : int
reference to non-polymorphic base: Base
reference to polymorphic base: Derived2
mydoubleptr points to double
bad_ptr points to...  caught std::bad_typeid
```