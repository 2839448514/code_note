---
tags:
  - CPP
---

# Smart Pointer(智能指针)

## `Smart Pointer`(智能指针)

自C++11起，C++标准库提供两大类型的`smart pointer`:

1. `Class shareed_ptr`实现共享式拥有(shared ownership) 概念。多个`smart pointer`可以指向相同指针，该对象和相关资源会在”最后一个`reference`被销毁”时释放。为了在结构复杂的情境中执行上述工作，标准库提供了`weak_ptr`、`bad_weak_ptr` 和 `enable_shared_from_this`等辅助类。

2. `Class unique_ptr`实现独占式拥有 (exclusive ownership) 或严格拥有 (strict ownership) 概念，保证同一时间内只有一个`smart pointer`可以指向该对象。你可以移交拥有权。他对于避免资源泄漏(resource leak)——例如“以new创建对象后因为发生异常而忘记使用delete”——特别有用。

   ```c++
   所有的smart pointer class都被定义于头文件<memory>内;
   ```

## `Class shared_ptr`

  我们需要当对象不再被使用时就被清理“的语义。`Class shared_ptr`提供了这样的共享式拥有语义。也就是说，多个shared_ptr可以共享同一对象。对象最末一个拥有者有责任销毁对象，并清理与该对象有关的所有资源。总之而言，shared_ptr的目的是在其对象不再被需要之后，自动释放与对象有关的资源。

```c++
#include <iostream>
#include<memory>
#include<string>
#include<vector>
using namespace std;
int main() {
    shared_ptr<string>pNico(new string("nico"));
    shared_ptr<string>pJutta(new string("jutta"));
    (*pNico)[0]='N';
    pJutta->replace(0,1,"J");
    vector<shared_ptr<string>>whoMadeCoffee;
    whoMadeCoffee.push_back(pJutta);
    whoMadeCoffee.push_back(pJutta);
    whoMadeCoffee.push_back(pNico);
    whoMadeCoffee.push_back(pJutta);
    whoMadeCoffee.push_back(pNico);
    for(auto ptr:whoMadeCoffee){
        cout<<*ptr<<" ";
    }
    cout<<endl;
    *pNico="Nicolai";
    for(auto ptr:whoMadeCoffee){
        cout<<*ptr<<" ";
    }
    cout<<endl;
    cout<<"use_count:"<<whoMadeCoffee[0].use_count()<<endl;
    return 0;
}
/*
Jutta Jutta Nico Jutta Nico 
Jutta Jutta Nicolai Jutta Nicolai 
use_count:4
*/
```

以下是对以上代码的说明：

```c++
shared_ptr<string>pNico(new string("nico"));
shared_ptr<string>pJutta(new string("jutta"));
//注意：”接受单一pointer作为唯一实参“的构造函数是explicit，所以这里你不能够使用赋值符，那么会被视为需要一个隐式转换。;
shared_ptr<string>pNico=new string("nico");//ERROE 错误的
shared_ptr<string>pNico(new string("nico"));//OK 正确的
//也可以使用便捷函数make_shared()，这种方式比较快也比较安全，它使用一次分配而不是二次分配;
shared_ptr<string> pNico=make_shared<string>("nico");
shared_ptr<string> pJutta=make_shared<string>("jutta");
//另外一种写法是先声明shared_pointer，然后对他赋值一个new pointer。然而你不可以使用assignment操作符，必须使用reset();
shared_ptr<string> pNico4;
pNico4=new string("nico");//ERROR:no assignment for ordinary pointers
pNico4.reset(new string("nico"));//OK
//由于但凡是容器，总是传入的元素创建属于自己容器的拷贝，所以我们直接安插string，插入的是string的拷贝。然而我们放入的是pointer to string ，被复制的是pointer，所以容器内有多个指向同一对象的reference。
//use_count()会产出”某个shared pointer所指对象“的当前拥有着数量，由于vector[0]指向的有4个：pJutta和他的三个拷贝，所以输出4。
cout<<"use_count:"<<whoMadeCoffee[0].use_count()<<endl;
```

## 定义属于自己的`delete`

定义自己的`delete`，让他在”删除被指向对象“之前先打印一条信息。

```c++
#include <iostream>
#include<memory>
#include<string>
#include<vector>
using namespace std;
int main() {
    shared_ptr<string> pNico(new string("nico"), [](string *p) {
        cout << "delete " << *p << endl;
        delete p;
    });
    shared_ptr<string> pJutta(new string("jutta"));
    (*pNico)[0] = 'N';
    pJutta->replace(0, 1, "J");
    vector<shared_ptr<string>> whoMadeCoffee;
    whoMadeCoffee.push_back(pJutta);
    whoMadeCoffee.push_back(pJutta);
    whoMadeCoffee.push_back(pNico);
    whoMadeCoffee.push_back(pJutta);
    whoMadeCoffee.push_back(pNico);
    for (auto ptr: whoMadeCoffee) {
        cout << *ptr << " ";
    }
    cout << endl;
    *pNico = "Nicolai";
    for (auto ptr: whoMadeCoffee) {
        cout << *ptr << " ";
    }
    cout << endl;
    cout << "use_count:" << whoMadeCoffee[0].use_count() << endl;
    return 0;
}
```

## 对付Array(数组)

请注意，`shared_ptr`提供的`default delete`调用的是`delete`，不是`delete[]`。这意味着只有当 `shared pointer` 拥有”由new建立起来的单一对象“，`default deleter`方能适才适所。为`array`建立一个`shared_ptr`是可能的，但是是错误的。

```c++
shared_ptr<int>p(new int[10]);//ERROR,but compiles(编译无误，运行错误)
```

所以，如果使用new[]建立一个`array of object`，必须定义自己的`delete`，不是`delete[]`。可以传入一个函数，函数对象或者`lambda`，让他们针对传入的寻常指针调用`delete[]`。

```c++
shared_ptr<int> p(new int[10], [](int *p) { delete[] p; });
//或者使用unique_ptr提供的辅助函数作为deleter，其内可调用deleter[]:
unique_ptr<int> p(new int[10],default_delete<int>[]());
```

但是，`shared_ptr`和`unique_ptr`以稍微不同的方式处理`deleter`。例如`unique_ptr`允许你只传递对应元素类型作为`template`实参，但对于`shared_ptr`就不行：

```c++
unique_ptr<int[]> p(new int[10]);//OK
shared_ptr<int[]> p(new int[10]);//ERROR:dose not compile
//此外，对于unique_ptr,你必须明确给予第二个template实参，指出你自己的deleter：
unique_ptr<int, void (*)(int *)> p(new int[10], [](int *p) { delete[] p; });
//注意，shared_ptr不提供operator[]。至于unique_ptr，他有一个针对array的偏特化版本，该版本提供了operator[]取代operator*和operator->。之所以有如此偏差，是因为unique_ptr在效能与弹性上做了优化。
```

## 其他析构策略

最末的一个拥有者——即`shared pointer`——结束生命时，如果清理工作不仅仅是删除内存，你必须明确给出自己的`deleter`。即指定自己的析构策略。

```c++
#include <iostream>
#include <memory>
#include <string>
#include <fstream>
#include <cstdio>
using namespace std;
class FileDelete {
private:
    string filename;
public:
    FileDelete(const string &fn) : filename(fn) {}
    // 删除器的操作符重载函数
    void operator()(ofstream *fp) {
        fp->close();  // 关闭文件流
        remove(filename.c_str());  // 删除文件
    }
};
int main() {
    // 创建带有自定义删除器的 shared_ptr，用于管理动态分配的 ofstream 对象
    shared_ptr<ofstream> fp(new ofstream("1.txt"), FileDelete("1.txt"));
    // 此时，当 shared_ptr 被销毁时，将调用 FileDelete 的操作符重载函数
    return 0;
}
```

## `Class weak_ptr`

`class weak_ptr`它用于解决 `shared_ptr` 的循环引用问题。当一个对象被 `shared_ptr` 所管理时，它的引用计数会增加，直到没有 `shared_ptr` 指向它时，它会被销毁。但是，如果存在循环引用，即两个或多个对象相互持有 `shared_ptr`，那么它们的引用计数永远不会归零，这可能导致内存泄漏。

`weak_ptr` 允许你访问由 `shared_ptr` 所管理的对象，但是不会增加引用计数。因此，即使存在循环引用，当所有 `shared_ptr` 都释放后，由 `weak_ptr` 所引用的对象也会被正确地销毁，因为它们不会阻止对象的释放。`weak_ptr` 通常用于解决指向对象的循环引用，或者当你需要引用一个 `shared_ptr` 所管理的对象，但不希望影响其生命周期时使用。  

`class weak_ptr`允许你共享但不拥有某个对象，这个`class`会建立起一个`shared pointer`。一旦最末一个拥有该对象的`shared pointer`失去了拥有权，任何`weak pointer`都会自动成为空。因此在`default`和`copy`构造函数之外，`class weak_ptr`只提供接受一个`shared_ptr`的构造函数。不能使用`*`和 `-> `操作符访问`weak_ptr`指向的对象，而是必须建立另外一个`shared pointer`。

```c++
#include <iostream>
#include <algorithm>
#include <vector>
#include <string>
#include <memory>
using namespace std;
class Person {
public:
    string name;
    shared_ptr<Person> mother;
    shared_ptr<Person> father;
    vector<shared_ptr<Person>> kids;
    Person(const string &n, shared_ptr<Person> m = nullptr, shared_ptr<Person> f = nullptr) : name(n), mother(m),father(f) {}
    ~Person() { cout << "delete" << name << endl; }
};
shared_ptr<Person> initFamily(const string &name) {
    shared_ptr<Person> mom(new Person(name + "'s mom"));
    shared_ptr<Person> dad(new Person(name + "'s dad"));
    shared_ptr<Person> kid(new Person(name, mom, dad));
    mom->kids.push_back(kid);
    dad->kids.push_back(kid);
    return kid;
}
int main() {
    shared_ptr<Person> p = initFamily("nico");
    cout << "- nico is shared " << p.use_count() << " times" << endl;
    cout << "- name of 1st kid is nico's mom: "
         << p->mother->kids[0]->name << endl;
    p = initFamily("jim");
    cout << "jim's family exists" << endl;
    return 0;
}
/*
- nico is shared 3 times
- name of 1st kid is nico's mom: nico
jim's family exists
*/
```

以上程序p是指向上述家庭最末的一个`handle`——也许是对p指派一个新的`person`或`reference`从kid指父母以及反面指向，因此，在p被赋值前，`nico`被共享了三次。现在如果，我们释放手上最末一个指向该家庭的`handle`——也许是对p指派一个新的`person`或一个`nullptr`，也许是`main()`结束时离开了p的作用域——没有任何`person`会被释放，因为它们都至少被一个`shared pointer`指向。于是析构函数未被打印。

```c++
#include <iostream>
#include <algorithm>
#include <vector>
#include <string>
#include <memory>
using namespace std;
class Person {
public:
    string name;
    shared_ptr<Person> mother;
    shared_ptr<Person> father;
    vector<weak_ptr<Person>> kids;
    Person(const string &n, shared_ptr<Person> m = nullptr, shared_ptr<Person> f = nullptr) : name(n), mother(m),father(f) {}
    ~Person() { cout << "delete" << name << endl; }
};
shared_ptr<Person> initFamily(const string &name) {
    shared_ptr<Person> mom(new Person(name + "'s mom"));
    shared_ptr<Person> dad(new Person(name + "'s dad"));
    shared_ptr<Person> kid(new Person(name, mom, dad));
    mom->kids.push_back(kid);
    dad->kids.push_back(kid);
    return kid;
}
int main() {
    shared_ptr<Person> p = initFamily("nico");
    cout << "- nico is shared " << p.use_count() << " times" << endl;
    cout << "- name of 1st kid is nico's mom: "
         << p->mother->kids[0].lock()->name << endl;
    p = initFamily("jim");
    cout << "jim's family exists" << endl;
    return 0;
}
/*
- nico is shared 1 times
- name of 1st kid is nico's mom: nico
deletenico
deletenico's dad
deletenico's mom
jim's family exists
deletejim
deletejim's dad
deletejim's mom
*/
```

如上，当我们`vector<weak_ptr<Person>> kids;`时，我们需要改变其访问对象的访问方式即`p->mother->kids[0].lock()->name`。

## 误用`Shared Pointer`

```c++
```

## 细究`shared pointer`与`weak pointer`

| 操作                              | 效果                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| `shared_ptr<T> sp`                | Default构造函数，建立一个`empty shared pointer`，使用`default delete`(也就是调用`delete`) |
| `shared_ptr<T> sp(ptr)`           | 建立一个`shared_pointer`令其拥有`*ptr`，使用`default delete`(也就是调用`delete`) |
| `shared_ptr<T>sp(ptr,del)`        | 建立一个`shared pointer`，令其拥有`*ptr`，使用`del`作为`delete` |
| `shared_ptr<T>sp(ptr,del,ac)`     | 建立一个`shared pointer`，令其拥有`*ptr`，使用`del`作为`delete`并以`ac`为`allocator` |
| `shared_ptr<T>sp(nullptr)`        | 建立一个`empty shared pointer`，使用`defult deleter`(调用`deleter`) |
| `shared_ptr<T>sp(nullptr,del)`    | 建立一个`empty shared pointer`，使用`del`作为`deleter`       |
| `shared_ptr<T>sp(nullptr,del,ac)` | 建立一个`empty shared pointer`，使用`del`作为`deleter`，并以ac为`allocator` |
| `shared_ptr<T>sp(sp2)`            | 建立一个`shared pointer`，与`sp2`共享所有权                  |
| `shared_ptr<T>sp(move(sp2))`      | 建立一个`shared pointer`，拥有`sp2`先前拥有的`pointer`(此后sp2将为`empty`) |
| `shared_ptr<T>sp(sp2,ptr)`        | `Alias`构造函数，建立一个`shared pointer`，共享`sp2`的所有权，但是指向`*ptr` |
| `shared_ptr<T>sp(wp)`             | 基于一个`weak pointer wp创建出一个`shared pointer`           |
| `shared_ptr<T>sp(move(up))`       | 基于一个`unique_ptr up创建出一个`shared pointer`             |
| `shared_ptr<T>sp(move(ap))`       | 基于一个`auto_ptr ap`创建出一个`shared pointer`              |
| `sp.~shared_ptr()`                | 析构函数，调用`deleter`——如果`sp`拥有一个对象                |
| `sp=sp2`                          | 赋值(此后`sp`将共享sp2的所有权，放弃向前所拥有对象的所有权)  |
| `sp=move(sp2)`                    | `Move assignment`(`sp2`将所有权移交给sp)                     |
| `sp=move(up)`                     | 赋予一个`unique_ptr up`(up将拥有权移交给sp)                  |
| `sp=move(ap)`                     | 赋予一个`auto_ptr ap`(ap将拥有权移交给sp)                    |
| `sp1.swap(sp2)`                   | 置换`sp1`和`sp2`的`pointer`和`deleter`                       |
| `swap(sp1,sp2)`                   | 置换`sp1`和`sp2`的`pointer`和`deleter`                       |
| `sp.reset()`                      | 放弃所有权并重新初始化`shared pointer`，使它像是`empty`      |
| `sp.reset(ptr)`                   | 放弃所有权并重新初始化`shared pointer`(拥有`*ptr`)，使用`defult deleter`(也就是调用`deleter`) |
| `sp.reset(ptr,del)`               | 放弃所有权并重新初始化`shared pointer`(拥有`*ptr`)，使用`del`作为`deleter` |
| `sp.reset(ptr,del,ac)`            | 放弃所有权并重新初始化`shared pointer`(拥有`*ptr`)，使用`del`作为`deleter`，并以`ac`为`allocator` |
| `make_shared(...)`                | 为一个新对象(以传出的实参为初值)建立一个`shared pointer`     |
| `allocate_shared(ac,...)`         | 为一个新对象(以传出的实参为初值)建立一个`shared pointer`，(使用`allocator ac`) |
| `sp.get()`                        | 返回存储的`pointer`(通常是被拥有物的地址；若不拥有对象则返回`nullptr`) |
| `*sp`                             | 返回拥有的对象(如果`none`则形成不确定行为)                   |
| `sp->...`                         | 为拥有者提供成员访问(如果`none`则形成不确定行为)             |
| `sp.use_count()`                  | 返回共享对象之拥有者数量(包括`sp`本身)，如果`shared pointer`是`empty`则返回0 |
| `sp.unique()`                     | 返回“`sp`是否为唯一拥有者”(等价于`sp.use_count()==1`)        |
| `if(sp)`                          | 操作符`bool()`，判断`sp`是否为`empty`                        |
| `sp1=sp2`                         | 针对存储的`pointer`(有可能是`nullptr`)调用`==`               |
| `sp1!=sp2`                        | 针对存储的`pointer`(有可能是`nullptr`)调用`!=`               |
| `sp1<sp2`                         | 针对存储的`pointer`(有可能是nullptr)调用`<`                  |
| `sp1<=sp2`                        | 针对存储的`pointer`(有可能是nullptr)调用`<=`                 |
| `sp1>sp2`                         | 针对存储的`pointer`(有可能是`nullptr`)调用`>`                |
| `sp1>=sp2`                        | 针对存储的`pointer`(有可能是`nullptr`)调用`>=`               |
| `static_pointer_cast(sp)`         | 对`sp`执行`static_cast<>`语义                                |
| `dynamic_pointer_cast(sp)`        | 对`sp`执行`dynamic_cast<>`语义                               |
| `const_pointer_cast(sp)`          | 对`sp`执行`const_cast<>`语义                                 |
| `get_delete(sp)`                  | 返回`deleter`的地址(如果有的话)，否则返回`nullptr`           |
| `strm<<sp`                        | 针对`sp`的`raw pointer`调用`output`操作符(相当于`strm<<sp.get()`) |
| `sp.owner_before(sp2)`            | 提供自己与另一个`shared pointer`之间的`strict weak`          |
| `sp.owner_before(sp2)`            | 提供自己与某个`weak pointer`之间的`tatic weak ordering`      |

`get_deleter()`会取得一个`pointer to deleter`(如果有定义`deleter`的话)，要不就去的`nullptr`。只要`pointer`还拥有那个`deleter`，该`pointer`就有效。但是为了取得·`deleter`，你必须以其类型作为`template`实参。

```c++
auto del = [](int *p) { delete p; };
shared_ptr<int> p(new int(10), del);
decltype(del) *pd = get_deleter<decltype(del)>(p);
```

## 更复杂的shared_ptr操作
