# Struct in C++

## Difference to `class` in C++
The **ONLY** difference between a `struct` and a `class` in C++ is that in `struct` member variables are `public` by default.

Struct can also have member methods.

## The `string` fields in struct
When a struct has a string filed:
```cpp
struct Something {
    string id;
}
```
Since in C++, it does not know how long a string will be, so a string filed will not be storing a **string text in the stack memory**, but instead it will store a **pointer to a string in the heap memory**. This will cause errors when we store a struck into a binary file since the copy of the string field will just be an address (namely a pointer) that pointers to no where in the new machine on which the binary file resides.

To make sure the fields stores a string text, we have to use **char array**:
```cpp
struct Something {
    char id[50];
}
```

