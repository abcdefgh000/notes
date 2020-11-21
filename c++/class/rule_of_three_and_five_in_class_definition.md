# Rule of Three in Class Definition

如果要定义以下三者其中任一个，则需要把这3个都定义了：
```cpp
// Destructor
~Class();

// Copy Constructor
Class(const Class &obj);

// Copy Assignment Operator
Class& operator = (const Class &obj);
```

# Rule of Five in Class Definition
With `move` semantics, the "Rule of 3" becomes "Rule of 5", since 
```cpp
// Move Constructor
// 1. `&&` 的意思是 RValue Reference
// 2. 括号里没有 `const` 是因为 move 会把 input param 变成 null
Class(Class &&obj);

// Move Assignment Operator
// 1. 这个 move assignment operator 和 copy assignment operator 很相像，都是 overwrite `=`
// 2. `&&` 的意思是 RValue Reference
// 3. 括号里没有 `const` 是因为 move 会把 input param 变成 null
Class& operator = (Class &&obj);
```
