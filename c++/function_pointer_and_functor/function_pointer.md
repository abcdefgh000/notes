# Function Pointer

Function pointer is a way to assign a function to a variable. The **name of a function** is actually **the pointer to the function**!

## Declare the Function Pointer, and use this Pointer to call the Function
```cpp
#include <iostream>

using namespace std;

int TwoSum(int num1, int num2) {
    return num1 + num2;
}

int main() {
    // Declare the function pointer.
    int (*fn_ptr_two_sum)(int, int) = TwoSum;
    
    // 或者也可以这样，语法上简单很多，意义和上面的一行 完全一样
    auto fn_ptr_two_sum = TwoSum;

    // Use the function pointer to call the function.
    cout << fn_ptr_two_sum(3, 5) << endl; // 8

    return 0;
}
```

## Declare a function that has an input param that is a pointer to another function
```cpp
int TwoSum(int num1, int num2) {
    return num1 + num2;
}

int TwoMulti(int num1, int num2) {
    return num1 * num2;
}

// 注意 这个函数的最后一个param，是如何把一个 pointer to function 作为一个 input param 的，
// 这个 pointer 里最后的 (int, int) 可以带 参数名，也可以不带，即 (int n1, int n2) 也行
int dealWithTwoNums(int num1, int num2, int (*input_function)(int, int)) {
    return input_function(num1, num2);
}

int main() {
    // 注意！调用 input function作为param 时，不再需要用 pointer to function！
    // 直接用 input function 的 function name 就可以！
    // (当然定义一个pointer to function 然后再用那个 pointer 在这里作为 param 也是可以的，但多此一举)
    cout << dealWithTwoNums(3, 5, TwoSum) << endl; // 8
    cout << dealWithTwoNums(10, 2, TwoMulti) << endl; // 20

    return 0;
}
```
