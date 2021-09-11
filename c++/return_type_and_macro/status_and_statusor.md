# Status and StatusOr


## 判断一个 status 是不是 某种特定类型的 Error
比如，判断一个 status 是否是 `NOT_FOUND` Error：
```cpp
auto status = ...
if (absl::IsNotFound(status)) {
  ...
}
```
