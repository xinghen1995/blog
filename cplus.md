## 主要内容
1. 对于C++这种面向对象的语言来说，函数传值必定会调用形参对象的构造函数(退出会调用析构函数)。这就增加了时间的开销，一次对象一般都是传递引用(const引用保证数据不被修改，即常量引用
)
2. C++用template声明泛型
```c++
template <class T, class Ta, class Tb, class Tc>
T abc(const Ta& a, const Tb& b, const Tc& c);
```
3. const引用返回。将返回引用声明为const，和普通的返回是一样的效果，不同在于要求函数返回值只能赋值给const常量。