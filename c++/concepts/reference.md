# Reference in C++

A reference is just an alias to the original variable.

```cpp
int a = 1;
int & ra = a;
```

`int & ra`, `int& ra` and `int &ra` are 100% the same to the compiler, since the compiler ignores all the spaces.
The difference between these 3 ways is just a matter of personal preference of styling.

不要认为 `int&` 连在一起代表任何意义，也不要认为 `&ra` 连在一起代表任何意义，它们谁靠近谁都完全没有意义。强行归纳只会庸人自扰。

用 `&` 这个符号来表达 reference，同时又用 `&` 来表达和 pointer 相关的 “取地址” 的概念，完全是 C++ 创造史上的一个悲剧。没有什么理由和原因。就是一个重复和偷懒的悲剧。

