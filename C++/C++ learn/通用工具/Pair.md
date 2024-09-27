## Pair操作函数

|                操作函数                 |                             影响                             |
| :-------------------------------------: | :----------------------------------------------------------: |
|              pair<T1,T2> p              | Default构造函数，建立一个pair，其元素类型分别为T1和T2，各自以其default构造函数初始化。 |
|        pair<T1,T2> p(vall,vall)         |    建立一个pair，元素类型分别为T1和T2，以vall和vall为初值    |
|         pair<T1,T2> p(rv1,rv2)          | 建立一个pair，元素类型分别为T1和T2，以rv1和rv2进行搬迁式初始化 |
| pair<T1,T2>p(piecewise,construct,t1,t2) | 建立一个pair，元素类型分别为tuple T1和T2，以tuple t1和t2的元素为初值 |
|            pair<T1,T2> p(p2)            |               Copy构造函数，建立p成为p2的拷贝                |
|            pair<T1,T2> p(rv)            |         Move构造函数，将rv的内容移至p(允许隐式转换)          |
|                  p=p2                   |             将p2的值赋值给p(C++11;允许隐式转换)              |
|                  p=rv                   |          将rv的值move assign给p(C++11;允许隐式转换)          |
|                 p.first                 |                    获得pair内的第一value                     |
|                p.second                 |                    获得pair内的第二value                     |
|                get<0>(p)                |                     等价于p.first(C++11)                     |
|                get<1>(p)                |                    等价于p.second(C++11)                     |
|                 p1==p2                  |                      返回“是否p1等于p2”                      |
|                 p1!=p2                  |                     返回“是否p1不等于p2”                     |
|                  p1<p2                  |                      返回“是否p1小于p2”                      |
|                  p1>p2                  |                      返回“是否p1大于p2”                      |
|                 p1<=p2                  |                    返回“是否p1小于等于p2”                    |
|                 p1>=p2                  |                    返回“是否p1大于等于p2”                    |
|               p1.swap(p2)               |                    互换p1与p2的值(C++11)                     |
|               swap(p1,p2)               |                   同上(是个全局函数;C++11)                   |
|          make_pair(val1,val2)           |           返回一个pair，带有val1和val2的类型和数值           |

自C++11开始，可以使用

```c++
tuple_size<IntFloatPair>::value;
tuple_element<0,IntFloatPair>::type;
pair<int, float> p = make_pair(0, 1);
// 输出pair对象的元素个数
cout << tuple_size<pair<int, float>>::value << endl;
// 输出pair对象第一个元素的类型信息
cout << typeid(tuple_element<0, pair<int, float>>::type).name();
```

实际上，`pair`是一个struct而不是class，以至于所有成员都是pubic:

```c++
namespace std{
    template <typename T1,typename T2>
    struct pair{
        T1 first;
        T2 second;
    }
}
```

想要实现泛型模板，将`pair`写入stream需要如下操作:

```c++
template<typename T1, typename T2>
std::ostream &operator<<(ostream &strm, const pair<T1, T2> &p) {
    return strm << "(" << p.first << ", " << p.second << ")";
}
pair<string, int>p[2] = {{"小明", 18},{"小红", 17}};
int main() {
    cout << p[0]<<endl<<p[1] << endl;
    return 0;
}
```