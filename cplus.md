## 导航
> #### 第二章 对象的创建和使用
> #### STL容器
> #### 随笔

## 第二章 对象的创建和使用
1. C语言的所有头文件在C++中都用c前缀声明，并省略'.h'的后缀：
```cpp
#include <cstdio>
#include <cstdlib>
```
2. <fstream.h>提供了文件操作的接口，主要式两个流式对象ifstream，ofstream。
3. getline()函数会丢弃换行符，而不是把它存入string对象。
4. 在C++中signed和unsigned比较会产生编译告警，可以使用std::size_t消除告警(for循环)

## 随笔
1. 对于C++这种面向对象的语言来说，函数传值必定会调用形参对象的构造函数(退出会调用析构函数)。这就增加了时间的开销，一次对象一般都是传递引用(const引用保证数据不被修改，即常量引用
)

2. C++用template声明泛型
```c++
template <class T, class Ta, class Tb, class Tc>
T abc(const Ta& a, const Tb& b, const Tc& c);
```

3. const引用返回。将返回引用声明为const，和普通的返回是一样的效果，不同在于要求函数返回值只能赋值给const常量。

## STL容器
1. <vector>
    + push_back() 在vector末尾添加一个元素
    + push_frount() 在vector前面加入一个元素
    + 取出元素直接使用书的数组下标，因为vector重载了数组访问运算符