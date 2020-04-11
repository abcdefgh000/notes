# Capture the "this" pointer in class

当 lambda expression capture一个 `this` pointer 的时候，是在 capture 一个 reference，所以这样的code是不合法的：
```cpp
// Cannot compile, since the `=` below means capture by value 
[=, this](){
    // ...
};
```

Ref: https://github.com/caveofprogramming/advanced-cplusplus/blob/master/CapturingThisWithLambdas/src/main.cpp

```cpp
#include <iostream>

using namespace std;

class Test {
private:
	int one { 1 };
	int two { 2 };

public:
	void run() {
		int three { 3 };
		int four { 4 };

		auto pLambda = [&, this]() {
			this->one = 11;
			cout << this->one << endl; // 11
			cout << this->two << endl;
			cout << three << endl;
			cout << four << endl;
		};
		pLambda();
	}

};

int main() {
	Test test;
	test.run();

	return 0;
}
```

