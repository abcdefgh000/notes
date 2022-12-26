# Structured Binding

Structured Binding 是一个 C++ 17 的功能。

举例：
```cpp
# include <tuple>

std::tuple<std::string, int> JustReturnSomething() {
  return { "Someone", 43 };
}

int main() {
  auto [name, age] = JustReturnSomething();
}
```

在 for loop 里的例子：
```cpp
std::vector<std::pair<std::string, int>> people = ...

for (auto [name age] : people) {
  std::cout << "Name: " << name;
  std::cout << "Age: " << age;
}
```
