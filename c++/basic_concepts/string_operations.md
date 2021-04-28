# String Operations

## 用 自定义的 间隔符 把一个 container 里的 elements 串起来
```cpp
std::vector<std::string> names = ...
absl::StrJoin(names, "\n")
```
上面 code 里的 vector 可以改为 set 等别的 container，也没问题。这个 code 运行出来的效果是：
```
element1
element2
element3
...
```
