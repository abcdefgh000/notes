# Overloading Assignment Operator

Assignment Operator `=` 原本的意义是 **Shallow Copy**。比如 `MyClass obj1 = obj2`，注意这里 obj1 和 obj2 都不是 reference，那么这里的 `=` 其实就是一个 shallow copy。
