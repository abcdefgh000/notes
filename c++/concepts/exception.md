# Exception in C++

## Custom Throw Content and Catch Content
The following example throws an integer and catches an integer.
```cpp
try {
  int age = 15;
  if (age >= 18) {
    cout << "Access granted.";
  } else {
    throw (age);
  }
} catch (int age) {
  cout << "Access denied - You must be at least 18 years old. While you are " << age;
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
    throw (500);
  }
} catch (...) {
  cout << "Access denied - You must be at least 18 years old." << age;
}
```
