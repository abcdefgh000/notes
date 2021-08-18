# Status 的用法

## 判断一个 status 是不是 某种特定类型的 error
比如，判断一个 status 是否是 `NOT_FOUND` error：
```cpp
auto status = ...

if (absl::IsNotFound(status)) {
  ...
}
```

