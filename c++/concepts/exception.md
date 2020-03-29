# Exception in C++

## Custom throw data type
The following example throws an integer and catches an integer.
```cpp
try {
    bool error1 = false;
    bool error2 = false;
    bool error3 = true;
    
    if (error1) {
        throw -1;
    } else if (error2) {
        throw "error2 occurred"; // This will be caught as a `char const *`
    } else if (error3) {
        throw string("error3 occurred"); // Don't use `new` here, this is special for exceptions in c++
    }
} catch (int e) { // The scope of `e` is only inside this one catch block
    cout << "error1 caught";
} catch (char const * e) {
    cout << "error2 caught";
} catch (string &e) { // A reference
    cout << "error3 caught";
}
```

## Handle any random type of Exception
Use the `(...)` inside the catch block to handle any type of known/unknown exception.
```cpp
try {
  int age = 15;
  if (age >= 18) {
    cout << "Access granted.";
  } else {
    throw 500;
  }
} catch (...) {
  cout << "Access denied - You must be at least 18 years old." << age;
}
```

## Custom Exception Class
```cpp
#include <iostream>
#include <exception>

using namespace std;

class CustomException: public exception {
  public:
    // This `what()` method is a method of the C++ `std::exception` base class.
    virtual const char* what() const throw() {
        return "Yo!";
    }
};

int main() {
    try {
        // Instantiate an object of the `CustomException` class,
        // and throw this object (namely this exception).
        throw CustomException();
    }
    catch(MyException &e) {
        cout << e.what() << endl;
    }
    
    return 0;
}
```
