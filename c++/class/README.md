# Class Overview

* **There is no such thing as a "Class", a so-called "Class" is just a bunch of functions with a hidden parameter** (我觉得这个 hidden parameter 就是一个identity，指向当前的 class instance) ---- The Cherno
  * 上面的说法换个方式说 就是：一个 class 里的每一个 non-static method always 自动地且偷偷地 gets an instance of the current class as a parameter。这是 class 的内部工作机制之一。
    * 这也是为什么 一个class的 static method 不能 access 这个class的 non-static field，因为 static method 不拥有任何 instance of the current class
