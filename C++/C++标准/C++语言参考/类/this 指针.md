---
tags:
  - CPP
---

# this 指针

### 语法

	**`this`**

---

关键词 `this` 是一个[[值类别|纯右值]][[表达式|表达式]]，其值是[[重载决议|隐式对象形参]]（在其上调用非静态成员函数的对象）的地址。它能出现于下列语境：

1) 在任何非静态[[非静态成员函数|成员函数]]体内，包括[[构造函数与成员初始化器列表|成员初始化器列表]]。

2) 在非静态成员函数的[声明](https://www.apiref.com/cpp-zh/cpp/language/function.html "cpp/language/function")中，（可选的）cv 限定符序列之后的任何位置，包括[[动态异常说明|动态异常说明](弃用)]]、[[noexcept 说明符 (C++11 起)|noexcept 说明]](C++11)以及尾随返回类型(C++11 起)

3) 在[[非静态数据成员|默认成员初始化器中]] (C++11 起)

在类 `X` 的成员函数中，`this` 的类型是 `X*`（指向 X 的指针）。若成员函数有 [[非静态成员函数|cv 限定]]，则 `this` 的类型是 `cv X*`（指向同一 cv 限定的 X 的指针）。因为构造函数与析构函数不能有 cv 限定，故它们之中 `this` 的类型始终是 `X*`，即使在构造或销毁 const 对象时也是如此。

当在任何允许 `this` 关键词的语境（非静态成员函数体、成员初始化器列表、默认成员初始化器）中使用非静态数据成员时，其名字之前会自动添加隐含的 `**this->**`，产生一个成员访问表达式（若该成员是虚成员函数，则产生虚函数调用）。

在类模板中，`this` 是一个[[待决名|待决表达式]]，而且显式的 `this->` 可以用于强行使另一表达式变为待决的。
