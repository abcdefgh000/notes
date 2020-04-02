# Overloading Assignment Operator

Assignment Operator `=` 原本的意义是 **Shallow Copy**。比如 `MyClass obj1 = obj2`，注意这里 obj1 和 obj2 都不是 reference，那么这里的 `=` 其实就是 把 obj2 的所有 fields shallow copy 到 obj1。如果obj2里有一个pointer，那么obj1里的同名pointer将会指向obj2里的那个pointer所指向的地址


