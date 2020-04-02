# Overloading Left Bit Shift Operator "<<" (for cout printing)

因为在 `cout << obj` 里，`<<`的左边是 `cout`，而我们如果要把 `<<` overload 成 class of obj 里的一个member function，而所有的 class member function的第一个parameter都必须（隐式地）是 这个class object 的 `this` pointer，所以`<<`是无法被 overload 成一个class里的member function的。我们只能把 `<<` 写成一个class里的 `friend function`。
