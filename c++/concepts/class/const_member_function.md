# Const Member Function in a Class

`const` member functions are functions that when called, they do not change the object calling them in any way.

A const member function can be called by a const object or non-const objext. a non-const functions can only be called by non-const objects.

Here is the syntax of const member function in C++ language:
```cpp
datatype functionName const();
```

```cpp
class Demo {
    int val;
  public:
     Demo(int x = 0) {
         val = x;
     }
     int getValue() const { // <=== const member function
         return val;
     }
};

int main() {
    const Demo d1(10);
    Demo d2(20);
   
    cout << "The value using object d1: " << d1.getValue();
    cout << "\nThe value using object d2: " << d2.getValue();
   
    return 0;
}
```
