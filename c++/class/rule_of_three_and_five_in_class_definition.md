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
Class(Class &&obj);
// Move Assignment Operator

```
