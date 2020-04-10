# Lambda Expression Overview

Lambda Expression 很像 function pointer and/or functor. 是 C++ 11 的新功能。

## Lambda Expression with no parameter and no return value
```cpp
#include <iostream>

using namespace std;

// void (*pLambdaExpression)() 的形式 很像 call 一个 function pointer，其中：
// 开头的 void 表示 这个 lambda expression 没有 return value，
// 结尾的 () 表示 这个 lamdba expression 没有 parameter，
// 中间的 (*pLambdaExpression) 里，* 表示这是一个指针，pLambdaExpression 这个名字是随意的，可以起任何名字
void runLambdaExpression(void (*pFunc)()) {
    pFunc();
}

int main() {
    // 定义一个 lambda expression 如下
    // 注意，一个 lambda expression 可以说就是 三个括号：一个 []，一个 ()，一个 {}
    auto lambdaExpression = []() { cout << "Hello" << endl; };

    // 直接 run 这个 lambda expression
    lambdaExpression(); // "Hello"
    
    // 用外面定义的 function 来 call 这个 lambda expression
    runLambdaExpression(lambdaExpression); // "Hello"

    // 一条龙，定义+直接call 一个 lambda expression 
    runLambdaExpression([]() {cout << "Hello again" << endl; }); // "Hello"

    return 0;
}
```

## Lambda Expression with parameter and no return value
```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

void runLambdaHi(void (*lamHi)(string)) {
    lamHi("Pete");
}

int main()
{
	// 有parameter 没有return value 的 lambda expression.
    auto lambdaHi = [](string name) { cout << "Hi " << name << '!' << endl;};
    
    lambdaHi("Ben"); // "Hi Ben!"
    
    runLambdaHi(lambdaHi); // "Hi Pete!"
    
    return 0;
}
```

## Lambda Expression with parameter and return value
```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

void runLambdaAdd(int (*lamAdd)(int a, int b)) {
    cout << lamAdd(9, 3) << endl;
}

int main()
{
	// 有parameter 也有 return value 的 lambda expression.
	// The `-> int` at the end means this lambda expression returns an int.
    auto lambdaAdd = [](int num1, int num2) -> int {
        return num1 + num2;
    };
    
    cout << lambdaAdd(1, 3) << endl; // 4

    runLambdaAdd(lambdaAdd); // 12
    
    return 0;
}
```
