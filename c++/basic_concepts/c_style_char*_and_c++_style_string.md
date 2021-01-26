# C Style `char*`, char array `char xxx[]`, C++ Style `string`

要弄明白 C++ 的 `std::string`，必须先弄明白 C style string 即 `char*`，以及 char array 即 `char xxx[]`。

关于以上三者 分别是如何work的 非常详细的视频教程：https://www.youtube.com/watch?v=ijIxcB9qjaU&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=32
* 包括它们在内存里的详细的 部署情况
* 在 `char*` 的末尾，系统会自动给你加一个 null 结束符。比如 程序员写 `const char* name = "Tiger";` 就可以了，但其实在最后的`r`的后面，系统会自动加一个 null 结束符
  * 一个null结束符 在内存里 就是一个 整数 `0` 或者 字符 `'\0'` 都可以，二者作用一样。如果自己手动写一个 `char name[6] = {'T', 'i', 'g', 'e', 'r', 0};`，那么就必须记得在最后手动加一个 结束符
  * 为什么 char* 的末尾要有 null 结束符，没有会怎么样
* `const char*` 和 `char*` 都可以，但大家更多地用 `const char*` 是因为 大家 在C里定义了一个串char以后，一般也不想再改动
  * 如果要改动，则不要用 `const char*` 而要用 `char*`
  * 当然现在其实大家都用 C++ 的 `std::string` 了
* C++ 的 `std::string` 其实就是一个 前面提到的 char array，再加上一些内置的 functionalities

