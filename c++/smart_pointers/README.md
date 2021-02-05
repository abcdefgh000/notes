# Smart Pointers Overview

A Smart Pointer is a Temlate Class that uses Operator Overloads to provide the functionality of a pointer, while providing improved memory management and safety.

A Smart Pointer is essentially a wrapper around a standard bare C language pointer. 这样就能让他实现上述优点的同时，还是可以 operate as close as a standard pointer.

Smart Pointer 里面比较基本的是 "Scoped Pointer"，unique pointer 也是 scoped pointer 进化而来的。现在好像更多地用 unique pointer 或者 shared pointer 了，不怎么用 scoped pointer 了。自己手写一个 scoped pointer 的话，是这个样子：
```
class CustomScopedPointer {
 public:
  CustomScopedPointer(Thing* thing_pointer) : thing_pointer_(thing_pointer) {}
  
  ~ CustomScopedPointer() { delete thing_pointer_; }
  
 private:
  Thing* thing_pointer;
};

class Thing {
  // ...
}
```

