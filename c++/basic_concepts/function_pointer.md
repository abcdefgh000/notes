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
