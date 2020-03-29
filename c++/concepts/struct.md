# Struct in C++

## Difference to class in C++
The **ONLY** difference between a `struct` and a `class` in C++ is that in `struct` member variables are `public` by default.

Struct can also have member methods.

## Struct cannot have `string` field
This is wrong:
```cpp
struct Something {
    string id;
}
```
