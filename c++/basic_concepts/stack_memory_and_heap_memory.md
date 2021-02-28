# Stack Memory and Heap Memory

一个很深入的关于 stack memory and heap memory 的 短视频教程：https://www.youtube.com/watch?v=wJ1L2nSIV1s&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=54

Stack memory 和 heap memory 都是 在 RAM 上的。并不是说 stack memory 在 CPU 缓存里。

Stack memory 里的 variables 的 addresses 都是紧贴着存在一起的（但是它们 两两之间会有几个 bytes 的 safety 间隔），详见下文。Heap memory 里的 variables 的 addresses 是散播各处的 不连续的。

如果使用 `new` key word，那么定义出来的 variables 就是在 heap memory 里面，如果使用 smart pointers，比如 `make_unique` 什么的，它们其实也是用了 `new`，只是在 `new` 的外面包了一层，所以 smart pointer 定义出来的 variables 也是在 heap memory 里的。 

## Stack Memory

“The idea of Stack Memory is: we literaly just stack things on top of each other, so a stack allocation is extremely fast, it's literally like one CPU instruction, all we do is we move the stack pointer and then we return the address of that stack pointer. That's it.”

---- The Cherno

Stack memory access 为什么这么快？因为内在机制上，程序在 stack memory 里读写 variables 的时候，写就是把所有的 stack variables 往一个连续的 RAM 区里扔，就和入栈出栈一样，读的时候就是 move stack pointer to 一个特定的地方，就把一个特定的variable 读出来了。所以这么快。

So, once the scope in which you've allocated that stack memory ends, all the memory you've allocated in that stack just **gets popped off**, 这里本质上发生的是：**the stack just moves to the position it used to be before we actually entered this scope!** 所以 这里就是 **这一块scope里的所有东西 作为一个整体 都被 pop 出栈了！**

## Heap Memory

