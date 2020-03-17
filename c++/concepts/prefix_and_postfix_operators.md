# Prefix and Postfix Operators

* Prefix Operator `++i`
  * Increment the value of `i`
  * Return a reference of `i`

* Postfix Operator `i++`
  * Create a copy of the variable `i`
  * Increment the value of `i`
  * Return the copied value from BEFORE the increment

So postfix operator is a tiny bit slower than the prefix operator in the same scenario.

Code example:
```cpp
#include<iostream>

using namespace std;

int main()
{
    int a, b = 0;
    int post, pre = 0;

    post = a++;
    pre = ++b;
    cout << post << "\n";   // 0
    cout << pre << "\n";    // 1
    cout << a << "\n";      // 1
    cout << b << "\n";      // 1
    
    return 0;
}
```
