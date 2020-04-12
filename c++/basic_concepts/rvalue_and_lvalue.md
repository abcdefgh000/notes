# RValue and LValue

`RValue` 和 `LValue` 的原始意思是字面上的左边/右边，比如 `int num = 7;` 里：`num` 在左边，是 LValue；`7` 在右边，是 RValue。

但现在 RValue 和 LValue 的意思已经根本性地变化了，**和左/右完全无关了，能“被取地址”的就是 LValue，不能的就是 RValue**。

关于 RValue：
* RValues are often temporary values
* Return values of functions are RValues，所以以下这样的code是不合法的：
  ```cpp
  Student getStudent(...) {
      ...
      return student1;
  }
  
  // 不合法，因为 getStudent 函数的返回值 是一个 RValue
  Student * pStudent = & getStudent(...);
  ```
* 
