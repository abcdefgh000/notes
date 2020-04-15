# Shared Pointer

Code ref: https://github.com/caveofprogramming/advanced-cplusplus/blob/master/SharedPointers/src/Shared%20Pointers.cpp
```cpp
#include <iostream>
#include <memory>
using namespace std;

class Test {
public:
	Test() {
		cout << "created" << endl;
	}

	void greet() {
		cout << "Hello" << endl;
	}

	~Test() {
		cout << "destroyed" << endl;
	}
};

int main() {

	shared_ptr<Test> pTest2(nullptr);

	{
		shared_ptr<Test> pTest1 = make_shared<Test>();

		pTest2 = pTest1;
	} // This is where pTest1 goes out of scope.

	cout << "Finished" << endl;
	return 0;
} // This is where pTest2 goes out of scope!
```
