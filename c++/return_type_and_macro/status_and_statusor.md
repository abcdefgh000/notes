# Status and StatusOr


## 判断一个 status 是不是 某种特定类型的 Error
比如，判断一个 status 是否是 `NOT_FOUND` Error：
```cpp
auto status = ...
if (absl::IsNotFound(status)) {
  ...
}
```

## Create 一个 特定 type 和 error message 的 status 用于 return 或 测试
```cpp
return absl::DataLossError("This is a funny error");
```
```cpp
absl::Status input_status_for_testing = absl::DataLossError("This is a funny error");
...
```
老式的做法（现在别这么用了）：
```cpp
absl::Status input_status_for_testing = 
    absl::Status(absl::StatusCode::kDataLoss, "This is a funny error");
```
