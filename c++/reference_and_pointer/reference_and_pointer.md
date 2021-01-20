# Reference and Pointer in C++
一个很棒的关于 pointer 和 reference 的 视频教程，这个教程的全系列我也放在 这个 C++ note folder 的 README.md 里了：
* Pointer: https://www.youtube.com/watch?v=DTxHyVn0ODg&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=16
* Reference: https://www.youtube.com/watch?v=IzoFn3dfsPA&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=17


## Pointer

### 声明指针
```cpp
int * int_ptr;
```

### 取地址
```cpp
int num = 1;
std::cout << &num; // 会显示 某长整数值，即地址值
```

### 声明指针并赋值
```cpp
int num = 1;
int * int_ptr = &num;
```

### "const pointer" and "pointer to const"
#### pointer to const variable
`const int*` 等效于 `int const*`，意思是：这个pointer所指向的东西的值不能变
```cpp
int some_int;
int const* int_ptr = &some_int; // somt_int 的值不能变

// 上面那个等效于下面这个：
const int* int_ptr = &some_int; 
```

#### const pointer
`int * const` 意思是：这个pointer不能再指向别的东西
```cpp
int some_int;
int * const int_ptr = &some_int; // int_ptr今生永远只能指向 some_int
```

### 用 pointer 作为函数的parameter
```cpp
int calculateSomething(string * strPtr, vector<string> * vecPtr);
```

#### const pointer to const variable
`const int* const` 等效于 `int const* const`，意思是：这个pointer永远不能再指向别的东西，而且这个pointer正在指向的这个东西的值也不能变。好凶。


### Pointer to Pointer
除了第一个以外，后面的越来越绕，作为memo就好不用记住
```cpp
// A pointer P1 to a pointer P2 to int
int **

// A const pointer P1 to a pointer P2 to an int，就是说P1所指向的pointer（即P2）不能变
int ** const

// A pointer p1 to a const pointer P2 to an int
int * const *

// A pointer P1 to a pointer P2 to a const int
int const **

// A const pointer P1 to a const pointer P2 to an (non-const) int
int * const * const
```

## Reference

*[The Cherno](https://www.youtube.com/channel/UCQ-W1KE9EYfdxhL6S4twUNw)* said:
* **A Reference is just a Pointer in disgise. References is just syntax sugar on top of Pointers**, so it's easier and cleaner to read and use. For example passing in a reference as an argument to a function is easier to write both in the caller function and callee function, compared to passing in a pointer.
* There is nothing you can do with a reference that you cannot do with a pointer. But pointers are more powerful than references.
* References do not really occupy memoery, they do not really have storage, they are not typical variables.

A reference is just an alias to the original variable. When we compile the code, we will only get one variable, which is the original variable, the reference is not a new variable, it's just an alias.

### 声明 reference

Once you declare a reference, you must immediately in the same statement refer it to a variable, you cannot do it later in another statement, namely:
```cpp
// Correct:
int num1 = 10;
int& ref_of_num1 = num1;

// Wrong:
int num2 = 20;
int& ref_of_num2;
ref_of_num2 = num2;
```

You cannot make that reference to refer to any other variable. Once declared, a reference sticks to that variable forever, so:
```cpp
int num1 = 10;
int num2 = 20;
int& ref = num1;

// 以下的code只是把 num2 的值 赋予给 num1，
// 而不可能做到 让 num1 的 reference 转而去 refer to num2
ref = num2;
```

特别注意！`int & ref_num`, `int& ref_num` and `int &ref_num` are 100% the same to the compiler, since the compiler ignores all the spaces。
The difference between these 3 ways is just a matter of personal preference of styling。**所以，不要认为 `int&` 连在一起代表任何意义，也不要认为 `&ref_num` 连在一起代表任何意义，它们谁靠近谁都完全没有意义。强行归纳只会庸人自扰**。

**用 `&` 这个符号来表达 reference，同时又用 `&` 来表达和 pointer 相关的 “取地址” 的概念，我认为，这完全是 C++ 创造史上的一个悲剧，我不知道有什么理由和原因，我觉得这就是一个重复和偷懒的悲剧**。

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
static std::vector<int> int_vec = {1, 2, 3};

std::vector<int> & doSomething(double ratio) {
    ...
    // modify the static int vector
    ...
    return int_vec;
}
```
注意！It's not legal to return a reference to local variable, since the local variable dies when leaving the local scope.


