# C++ 构造函数、析构函数 、拷贝构造函数

## 一、构造函数

* 在创建对象时，会自动调用并初始化
* 其他的懂的都懂，不需要多说

## 二、析构函数

* 对象的清理，当对象的生命周期结束时，就直接释放。

* 在以下情况下会自动调用：

  1.如果一个对象定义在一个函数体内，则当该函数结束时，该对象的析构函数就会自动被调用。

  2.若一个对象是使用new运算符动态创建的(new调用构造函数)，在使用delete运算副释放对象时，delete会自动调用析构函数。

## 三、拷贝构造函数

* 以下三种情况会自动调用拷贝构造函数：

  1.当用一个类的对象初始化另外一个对象时。

  2.当函数的形参为类的对象，将对象作为函数实参传递给函数的形参时。

  3.当函数的返回值是类的对象、创建临时对象时。

```c++
#include<iostream>
using namespace std;
class Student
{
private:
    string name;
    string sex;
    int age ;
public:
    Student(string n , string s, int a )
    {
        name = n;
        sex = s ;
        age = a;
    }
    Student(Student & obj)
    {
        name = obj.nane;
        sex = obj.sex;
        age = obj.age;
        cout << "调用拷贝 ." << endl;
    }
    ~Student()
    {
        cout << "调用析构函数：" << name <<endl ; 
    }
}
```

