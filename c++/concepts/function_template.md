# Function Template

The `T` is just a symbol, we can use any char or string like `S`, `s`, `hey`, `heyThere123` to replace `T`.

```cpp
// Tell the compiler we are using a template. T represents the variable type.
template <typename T>
T getSmaller(T  input1,T  input2) {
    if(input1 < input2) {
        return input1;
    }
    return input2;
}
```

```cpp
std::cout << "Integers compared: " << getSmaller(1, 3) << "\n";
std::cout << "Floats compared: " << getSmaller(1.5, 3.5) << "\n";
std::cout << "Chars compared: " << getSmaller('h', 'g') << "\n";
std::cout << "Strings compared: " << getSmaller("Hey guys!", "Hey ladies!") << "\n";  
```
