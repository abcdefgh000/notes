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

上面的code会输出：
```
created
Finished
destroyed
```
因为 pTest2 的 de-allocate of memory 是发生在 main function 的结尾 } 处的，即发生在 print "Finished" 的后面
