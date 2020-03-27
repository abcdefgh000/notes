# Reference and Pointer in C++

## Reference

A reference is just an alias to the original variable.

### 声明 reference
```cpp
int num = 1;
int & ref_num = num;
```

`int & ref_num`, `int& ref_num` and `int &ref_num` are 100% the same to the compiler, since the compiler ignores all the spaces.
The difference between these 3 ways is just a matter of personal preference of styling.

不要认为 `int&` 连在一起代表任何意义，也不要认为 `&ref_num` 连在一起代表任何意义，它们谁靠近谁都完全没有意义。强行归纳只会庸人自扰。

用 `&` 这个符号来表达 reference，同时又用 `&` 来表达和 pointer 相关的 “取地址” 的概念，完全是 C++ 创造史上的一个悲剧。没有什么理由和原因。就是一个重复和偷懒的悲剧。

### 用reference作为函数的parameter，并如何call这样的函数
```cpp
void modifyString(string & str) {
    // ...
}

string str = "Hey Guys!";
modifyString(str);
```

### return 一个 reference
```cpp

```

## Pointer

### 取地址
```cpp
int num = 1;
std::cout << &num; // 某长整数
```
### 声明指针
```cpp
int * int_ptr;
```

### 声明指针并赋值
```cpp
int num = 1;
int * int_ptr = &num;
```
