# Overloading Assignment Operator

Assignment Operator `=` 原本的意义是 **Shallow Copy**。比如
```cpp
MyClass obj2;
obj2 = obj1;
````
注意这里 obj1 和 obj2 都不是 reference，那么这里的 `=` 其实就是 把 obj1 的所有 fields shallow copy 到 obj2。如果obj1 里有一个pointer，那么obj2里的同名pointer将会指向obj1里的那个pointer所指向的地址。

特别注意：上面2句statement 的内在机制与 `MyClass obj2 = obj1;` 不同！后者里面的 `=` 其实是是 copy constructor！而不是一个 assignment operator！所以如果我们 overload assignment operator，不会影响 `MyClass obj2 = obj1;`

上面的2句statements 等价于下面这个code（只是很少有人像下面这么写）：
```cpp
MyClass obj2;
obj2.operator=(obj1);
```

所以上面的2句statements里，**assignment operator `=` 可以算是 obj2 的一个member function，它有一个explicit的 input paramter obj1，还有一个 implicit input parameter 就是 `this` pointer of obj2，这个function还有一个return 值，就是 obj2 的 const reference!** 

所以这个statement是 valid的：`obj3 = obj2 = obj1;`，它的意思是：
* 先做 `obj2 = obj1`，即 从obj1 的 const reference 进行 shallow copy 得到 obj2
* 再做 `obj3 = obj2`，即 从obj2 的 const reference 进行 shallow copy 得到 obj3

An example of copy constructor and overloading assignment operator:
```cpp
#include <iostream>
#include <string>

using namespace std;

class Test
{
  int id; 
	string name;

  public:
	Test() : id(0), name("")
	{
		
	}

	Test(int id, string name) : id(id), name(name)
	{
		
	}

	Test(const Test& other)
	{
		cout << "Copy constructor running" << endl;
		this->id = other.id;
		this->name = other.name;
	}

	const Test& operator=(const Test &other) {
		cout << "Assignment running" << endl;
		this->id = other.id;
		this->name = other.name;
		return *this;
	}
	
	void print() const
	{
		cout << id << ": " << name << endl;
	}
};
```
