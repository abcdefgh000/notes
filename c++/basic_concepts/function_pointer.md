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

int dealWithTwoNums(int num1, int num2, int (*inputFunction)(int, int)) {
    return inputFunction(num1, num2);
}

int main() {
    // Declare the function pointers.
    int (*ptrTwoSum)(int, int) = twoSum;
    int (*ptrTwoMulti)(int, int) = twoMulti;

    cout << dealWithTwoNums(3, 5, ptrTwoSum) << endl; // 8
    cout << dealWithTwoNums(10, 2, ptrTwoMulti) << endl; // 20

    return 0;
}
```
