# Function Template

```cpp
// Tell the compiler we are using a template.
template <typename T>
T getSmaller(T  input1,T  input2) {
    if(input1 < input2) {
        return input1;
    }
    return input2;
}
```

```cpp
std::cout << "Integers compared: " << getSmaller(a,b) << "\n";
std::cout << "Floats compared: " << getSmaller(f1,f2) << "\n";
std::cout << "Chars compared: " << getSmaller(c1,c2) << "\n";
std::cout << "Strings compared: " << getSmaller(s1,s2) << "\n";  
```
