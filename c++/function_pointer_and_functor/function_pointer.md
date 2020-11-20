# Function Pointer

The **name of a function** is actually **the pointer to the function**!

## Declare the Function Pointer, and use this Pointer to call the Function
```cpp
#include <iostream>

using namespace std;

int twoSum(int num1, int num2) {
    return num1 + num2;
}

int main() {
    // Declare the function pointer.
    int (*ptrTwoSum)(int, int) = twoSum;

    // Use the function pointer to call the function.
    cout << ptrTwoSum(3, 5) << endl; // 8

    return 0;
}
```

## Declare a function that has an input param that is a pointer to another function
```cpp
int twoSum(int num1, int num2) {
    return num1 + num2;
}

int twoMulti(int num1, int num2) {
    return num1 * num2;
}

// 注意 这个函数的最后一个param，是如何把一个 pointer to function 作为一个 input param 的，
// 这个 pointer 里最后的 (int, int) 可以带 参数名，也可以不带，即 (int n1, int n2) 也行
int dealWithTwoNums(int num1, int num2, int (*inputFunction)(int, int)) {
    return inputFunction(num1, num2);
}

int main() {
    // 注意！调用 input function作为param 时，不再需要用 pointer to function！
    // 直接用 input function 的 function name 就可以！
    // (当然定义一个pointer to function 然后再用那个 pointer 在这里作为 param 也是可以的，但多此一举)
    cout << dealWithTwoNums(3, 5, twoSum) << endl; // 8
    cout << dealWithTwoNums(10, 2, twoMulti) << endl; // 20

    return 0;
}
```