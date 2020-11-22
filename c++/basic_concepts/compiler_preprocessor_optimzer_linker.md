# Compiler (含有 Preprocessor, Compiler, Optimizer, Linker)

Compiler 是把 source code 转化为 exexutable binary 的.

Compiler 里面含有：
* Preprocessor, 注意 这个发生在 compilation 之前！
* Compiler
* Optimizer
* Linker

## Preprocessor
Preprocessor 处理这些东西：
* `#include` files
  * code里使用 `#include ...` directive 的时候，source file 会把 被include的file的全部内容 直接复制粘贴到 `#include ...` directive 所在的地方
* Preprocessor Macros, 比如
  * `#define`，这其实就是简单的 string substitution in the source file
    * 有人会用 `#define` 来定义 preprocessor 层面的 constants。但其实这不是 good practice，因为这样做其实不是定义了constant，只是定义了一个 string replacement 的 macro。示例代码：
      * `#define PI 3.14`，这类语句后面没有 `;`，因为 preprocessor 有自己的语法，不同于C或者C++的语法
  * `#ifndef` + `#define` + `#endif`



## Compiler



## Optimizer



## Linker


