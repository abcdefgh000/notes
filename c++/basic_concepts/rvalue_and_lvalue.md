# RValue and LValue

## 定义

**LValue 是 拥有存储地址（也即可以 被 取地址）的东西**。RValue 是 不拥有存储地址 的东西。

举例：

```cpp
int i = 10;
```

In the above example, `i` is an LValue and `10` is an `RValue`, we can never do `10 = i`, 因为 i 拥有自己的地址，而 10 不可能有自己的地址。

所以 `L/R`Value **和 它们处于 等号的 左/右 完全无关**，只和上面说的 “它们是否拥有地址” 有关.

## RValue 可以是一个函数的返回值

```cpp
int GetAThing() {
  return 10;
}

int main() {
  int thing = GetAThing();
}
```
在上面的例子里，`GetAThing()` 这个函数 返回了一个 RValue 10，这个 RValue 是一个 temporary value，它 has no storage，no location。

然后我们 take this RValue and store it into an LValue `thing`。

同上理，如果我们写 `GetAThing() = 11` 是不可以的，因为 `GetAThing()` 返回的是一个 RValue，它 没有也不可以有 自己的地址。

==================

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
* `num++` 会搞出来一个 temporary variable，而 temporary variable 是无法被取地址的，所以下面的code是不合法的，即`num++`是 RValue
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
Student student1;
Student & refStudent1 = student1;
```
但如下的code是不合法的，原因和上文同理：因为 getStudent 函数的返回值 是一个 RValue：
```cpp
// 不合法
Student & refStudent1 = getStudent(...);
```
但加个 const 就行了：
```cpp
// 合法
const Student & refStudent1 = getStudent(...);
```

### RValue Reference
LValue Reference 不能用于 RValue。但是有专门的 RValue Reference 用于 RValue，code如下：
```cpp
// 以下2个都是合法的
Student && student1 = getStudent(...);
Student && student1 = Student(); // Student() is a Constructor of the Student class.
```
这里的 `&&` 就是 RValue Reference 的意思，2个连续的 & 在这个语境下就是特化为这个意思，并不是 reference of reference 的意思，也没有别的意思。

RValue Reference 作为函数的输入参数：
```cpp
// Input param 是 LValue Reference
bool check1(const Student && student) {
    ...
}

// Input param 是 RValue Reference，
// RValue Reference 做参数的时候一般不带 const，因为此函数往往要修改输入的参数
bool check2(Student && student) {
    ...
}

Student student1;
Student & lRefStudent = student1;
check1(lRefStudent);

check2(getStudent(...));
check2(Student())
```




