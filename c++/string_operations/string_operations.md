# String Operations

## 查看 一个 string 里是否含有 某个 sub string
```cpp
absl::StrContains(look_in_string, look_for_sub_string)
```

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

## Check 一个 string 的 prefix 和 suffix
```cpp
bool has_prefix = absl::StartsWith(target_string, prefix);

bool has_suffix = abls::EndsWith(target_string, suffix);
```
