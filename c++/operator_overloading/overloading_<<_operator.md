# Overloading Left Bit Shift Operator "<<" (for cout printing)

在 `cout << obj` 里，`<<`的左边是 `cout`，右边是 `obj`。但我们如果要把 `<<` overload 成 class of obj 里的一个member function 的话，所有的 class member function的第一个parameter都必须（隐式地）是 这个class object 的 `this` pointer，而不可以作为第二个 parameter 出现在 function的parameter list 里，所以`<<`无法被 overload 成 隐含 `this`的 member function，而必须 显示地 含有 `obj` 作为第二个 param，并且弄一个 `ostream` 作为第一个 param。

另外，因为原版的 `<<` 会返回一个 `ostream`（因此我们才能 chain 一串 `cout << a << b;`），所以 我们 overload 的 `<<` 也必须return 一个 ostream。

```cpp
class P
```
