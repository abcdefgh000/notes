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
* `num++` 会搞出来一个 temporary variable，而 temporary viable 是无法被取地址的，所以下面的code是不合法的，即`num++`是 RValue
  ```cpp
  int num = 1;
  // 下面两行code不合法
  int * pNum = &num++;
  int * pNum = &(num++);
  ```
* `(num + 7)` 这样的东西也是RValue，无法被取地址
  ```cpp
  // num 是 LValue
  int num = 1;
  // 下面这些code不合法，因为 (num + 7) 和 (7 + num) 都是 RValue
  int * pNum = &(num + 7);
  int * pNum = &(7 + num);
  ```

## LValue Reference and RValue Reference

### LValue Reference
C++里一般的reference就是 LValue Reference，比如：
```cpp
Student & rStudent1 = student1;
```
但如下的code是不合法的，原因和上文同理：因为 getStudent 函数的返回值 是一个 RValue：
```cpp
// 不合法
Student & rStudent1 = getStudent(...);
```
但加个 const 就行了：
```cpp
// 合法
const Student & rStudent1 = getStudent(...);
```


### RValue Reference

