# c-practice
编译的时候加上-std=-std=gnu++0x.例：g++ -std=gnu++0x -o he he.cpp
练习C++
只有用static修饰的成员函数才可以不用申明对象，直接用类：：函数的形式访问
例子：
class tim{
static void pri(void)
{
cout<<"fsdadfd"<<endl;
}
};
可以直接调用tim::pri函数运行。
STL容器：
我们能够定义的容器的类型有三个限制：

1元素类型必须支持等于操作符；（对于类类型struct或class，即指等于号==重载）

2、元素类型必须支持小于操作符；（对于类类型struct或class,即指小于号<重载

3、元素类型必须支持一个缺省值（对于类类型，即指缺省构造函数）；

例子：
struct people{
	int age;
	int sextype;
	char name[20];
	bool operator<(const cont &man) const
	{
		return age<man.age;
	}
	bool operator==(const cont &ma) const
	{
		return sextype==ma.sextype;
	}
};

如果要把静态成员数据设为私有，该如何访问？
通过公有成员函数访问。
注意：设置了静态成员变量，要给静态成员变量初始化

初始化列表的初始化变量顺序是根据成员变量的声明顺序来执行的。

虚函数就是允许被其子类重新定义的成员函数。
虚函数采用了一种虚调用的方法，虚调用是一种可以在 只有部分信息的 情况下 工作的机制，特别允许我们调用一个只知道接口而不知道其 准确类型的函数，但是如果要创建一个对象，你势必要知道对象的准确类型，因此构造函数不能为空
虚函数是非常有效的，但不能把每一个函数都声明为虚函数.
因为虚函数是有代价的，由于每个虚函数的对象都需要维护一个V表，因此使用虚函数时会产生额外的系统开销，如果是一个很小的类，且不想派生其他的类，那么根本没有必要使用虚函数。

子类重新定义父类虚函数的做法，称为重写。
重写的函数必须有一致的参数表和返回值。
重载是指编写一个与已有函数同名但是参数表不同的函数

宏，内联函数，模板都可以在编译时解析，但是虚函数不可以，他必须在运行时才能确定

多态是通过继承和虚函数实现的

类中的线程函数都必须是静态的， 因为非静态成员函数都会在参数列表中加上一个this指针为为参数, 这样的话你写的线程函数就不符合调用规定了.
这也说明为什么静态函数不能直接调用非静态变量

在静态成员函数的实现中不能直接引用类中说明的非静态成员，可以引用类中说明的静态成员（这点非常重要）。
如果静态成员函数中要引用非静态成员时，可通过对象来引用。从中可看出，调用静态成员函数使用如下格式：<类名>::<静态成员函数名>(<参数表>);

注意map::erase和vector::erase非常不一样，一定要注意
*只要定义了任何构造函数，编译器就不会生成默认构造函数，如果没有定义复制构造函数，编译器就会生成复制构造函数。
*无论什么时候在类中动态分配了内存，都应该编写自己的复制构造函数和赋值运算符，以提供深层的内存复制。
*在类中被const声明的成员函数只能访问const成员函数，而非const函数可以访问任意的成员函数，包括const成员函数
*基类的指针或者引用指向派生类时，派生类保留其重写方法。但是通过类型转换将派生类对象转换为基类对象时，就会丢失其特征，重写方法和派生类数据的丢失称为截断。（注意主要看类的对象是基类还是派生类）
