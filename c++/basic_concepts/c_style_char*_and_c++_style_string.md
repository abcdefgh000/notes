# C Style `char*`, `char xxx[]`, C++ Style `string`

要弄明白 C++ 的 `std::string`，必须先弄明白 C style string 即 `char*`，以及 char array 即 `char xxx[]`。

关于以上三者 分别是如何work的 非常详细的视频教程：https://www.youtube.com/watch?v=ijIxcB9qjaU&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=32
* 包括它们在内存里的详细的 部署情况
* 为什么 char* 的末尾要有 null 结束符，没有会怎么样
* `const char*` 和 `char*` 都可以，但大家更多地用 `const char*` 是因为 在C里大家定义了一个所谓的“string”以后一般也不想再改动。如果要改动，则不要用 `const char*` 而要用 `char*`。当然现在其实大家都用 C++ 的 `std::string` 了


