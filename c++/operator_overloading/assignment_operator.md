# Overloading Assignment Operator

Assignment Operator `=` 原本的意义是 **Shallow Copy**。比如 `MyClass obj1 = obj2`，注意这里 obj1 和 obj2 都不是 reference，那么这里的 `=` 其实就是 把 obj2 的所有 fields shallow copy 到 obj1。如果obj2里有一个pointer，那么obj1里的同名pointer将会指向obj2里的那个pointer所指向的地址.

实际上，`MyClass obj1 = obj2` 是等价于下面这个code的（只是很少有人像下面这么写罢了）：
```cpp
MyClass obj1;
obj1.operator=(obj2);
```

所以上面的例子里，**assignment operator 可以看作是 obj1 的一个member function，它有一个explicit的 input paramter obj2，还有一个 implicit input parameter 就是 `this` pointer of obj1，这个function还有一个return 值，就是 obj1 的reference!** 所以我们可以这么写：`obj3 = obj1 = obj2;`，它的意思就是 先做 `obj1 = obj2`，再做 `obj3 = obj1`。


