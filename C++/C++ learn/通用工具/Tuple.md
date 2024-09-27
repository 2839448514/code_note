## Tuple(不定数的值组)

|                  操作                  |                             效果                             |
| :------------------------------------: | :----------------------------------------------------------: |
|         tuple<T1,T2,...,Tn> t          | 以n个给定类型的元素建立一个tuple，以个元素类型的default构造函数完成初始化(基础类型初始化为0) |
| tuple<T1,T2,...,Tn> t(vl1,vl2,...,vln) |     以n个给定类型的元素建立一个tuple，以给定值完成初始化     |
|           tuple<T1,T2> t(p)            | 建立一个tuple，带有两个元素，分别使用给定类型，并以给定之pair p为初值(类型必须吻合) |
|                  t=t2                  |                         将t2赋值给t                          |
|                  t=p                   |  将pair p赋值给一个带两个元素的tuple(pair p的类型必须吻合)   |
|                 t1==t2                 |                      返回“是否t1等于t2”                      |
|                 t1!=t2                 |                     返回“是否t1不等于t2”                     |
|                 t1<t2                  |                      返回“是否t1小于t2”                      |
|                 t1>t2                  |                      返回“是否t1大于t2”                      |
|                 t1<=t2                 |                    返回“是否t1小于等于t2”                    |
|                 t1>=t2                 |                    返回“是否t1大于等于t2”                    |
|              t1.swap(t2)               |                   互换t1和t2的数据(C++11)                    |
|              swap(t1,t2)               |                    同上(是全局函数;C++11)                    |
|         make_tuple(v1,v2,...)          | 以传入的所有数值和类型建立一个tuple，并允许由此tuple提取数值 |
|             tie(ref1,ref2)             | 建立一个由reference构成的tuple，并允许由此tuple提取个别数值  |

#### 便捷函数make_tuple和tie()

```c++
tuple<int, float, string> t = make_tuple(12, 12.1, "hello");
auto t1 = tie(t);
int main() {
    cout << get<0>(t) << endl;
    cout << get<1>(t) << endl;
    cout << get<2>(t) << endl;
    // 使用 tie 返回的元组引用来获取元组的值
    int intValue;
    float floatValue;
    string stringValue;
    tie(intValue, floatValue, stringValue) = t;=
    // 输出元组的值
    cout << "Int Value: " << intValue << endl;
    cout << "Float Value: " << floatValue << endl;
    cout << "String Value: " << stringValue << endl;
    return 0;
}
```

#### 其他tuple特性

```c++
tuple_size<tupletype>::value可获得元素个数;
tuple_element<idx,tupletype>::type可获得第idx个元素类型(也就是get()的返回值);
tuple_cat()可将多个tuple串接成为一个tuple
```

#### Tuple的输入输出

```c++

```