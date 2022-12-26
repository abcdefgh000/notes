# RValue and LValue 的定义

Great video about RValue and LValue: https://www.youtube.com/watch?v=fbYknr-HPYE&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=85&app=desktop

**LValue 是 拥有存储地址（也即可以 被 取地址）的东西**。RValue 是 不拥有存储地址 的东西。

举例：

```cpp
int i = 10;
```

In the above example, `i` is an LValue and `10` is an `RValue`, we can never do `10 = i`, 因为 i 拥有自己的地址，而 10 不可能有自己的地址。

所以 `L/R`Value **和 它们处于 等号的 左/右 完全无关**，只和上面说的 “它们是否拥有地址” 有关.

所以 **RValue 往往被认为是 temporary value**。

# RValue 可以是一个函数的返回值

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

# 一个函数 可以返回 LValue，即返回一个 LValue reference

C++里一般的reference就是 LValue Reference，比如：
```cpp
Student student1;
Student & refStudent1 = student1;
```

如下这么做就可以返回一个 LValue Reference：

```cpp
int& GetAThing() {
  static int a_thing = 10;
  return a_thing;
}

int main() {
  GetAThing() = 11;  // <=== This is ok to do now!
}
```

# An LValue can be created by an RValue

Example:
```cpp
void SetValue(int value) {
  int hey = value;
}

int main() {
  SetValue(10);  // 10 is an RValue, it's used to create an LValue `hey` inside `SetValue(...)`.
}
```

# We cannot create a non-const LValue Reference from an RValue

So we can only create a non-const LValue Reference form an LValue. The following call of `SetValue(10)` does NOT work:

```cpp
void SetValue(int& value) {  // Now this function is taking an LValue Reference as param.
  int hey = value;
}

int main() {
  SetValue(10);  // Now this does NOT work since 10 is an RValue, it does not have an address.
}
```

Another example that does NOT work for the same reason:
```cpp
int& a = 10;  // Does NOT work since 10 is an RValue that doesn't have an address.
```

# We can create a `const` LValue Reference from an RValue
This works (it's actually kind of a workaround):
```cpp
const int& a = 10;  // Works!! Since now `a` is a CONST LValue Reference.
```

What really happened here was:
```cpp
int temp = 10;
const int& a = temp;
```
1. The Compiler creates a temporary variable with the actual storage
2. Assign the value 10 to the tempraroy variable
3. Assign the tempraroy variable to the `const` LValue Reference `a`.

So, for the same reason, the following will work:
```cpp
void SetValue(const int& value) {  // A const LValue Reference.
  int hey = value;
}

int main() {
  SetValue(10);  // Works now.
}
```

# A function that only accepts LValue Reference

```cpp
int main() {
  std::string first_name = "Pig";
  std::string last_name = "King";

  std::string full_name = first_name + last_name;
}
```
In the above code, the expression `first_name + last_name` is an RValue and a temprary object. What happened is: a temporary string got constructed from `first_name + last_name` and then this temporary string got assigned to the LValue `full_name`.

So:
```cpp
void PrintName(std::string& name) {  // Expect an LValue Reference to be input here.
  std::cout << name << std::endl;
}

int main() {
  std::string first_name = "Pig";
  std::string last_name = "King";
  std::string full_name = first_name + last_name;  
  
  PrintName(full_name);  // Works, since full_name is an LValue.
  PrintName(first_name + last_name);  // Does NOT work here, since the input cannot be an RValue.
}
```

# RValue Reference only takes in RValue object
Example: `std::string&& name` in the following function is an **RValue Reference**, it only accepts RValue.

这里的 `&&` 就是 RValue Reference 的意思 (2个连续的 & 在这个语境下就是特化为这个意思，并不是 reference of reference 的意思，也没有别的意思)。

```cpp
void PrintName(std::string&& name) {  // Only accepts RValue to be input here.
  std::cout << name << std::endl;
}

int main() {
  std::string first_name = "Pig";
  std::string last_name = "King";
  std::string full_name = first_name + last_name;  
  
  PrintName(full_name);  // Does NOT work here, since the input cannot be an LValue.
  PrintName(first_name + last_name);  // Works here.
}
```

# `const` LValue Reference can take in either LValue object or RValue object
As we mentioned above, `const &` can accept everything：
```cpp
void PrintName(const std::string& name) {  // `const` LValue Reference can accept both LValue/RValue to be input here.
  std::cout << name << std::endl;
}

int main() {
  std::string first_name = "Pig";
  std::string last_name = "King";
  std::string full_name = first_name + last_name;  
  
  PrintName(full_name);  // Works.
  PrintName(first_name + last_name);  // Works.
}
```
