# Status and StatusOr


## 判断一个 status 是不是 某种特定类型的 Error
比如，判断一个 status 是否是 `NOT_FOUND` Error：
```cpp
auto status = ...
if (absl::IsNotFound(status)) {
  ...
}
```
古法（现在别这么用了）：
```cpp
status.code() == 某种 error type enum
```

## 判断一个 statusor 是否是 ok
直接用：
```cpp
StatusOr<xxx> foo = ...
if (foo.ok()) {
  ...
}
```
不要用：
```cpp
if (foo.status().ok()) {
  ...
}
```

## Create 一个 特定 type 和 error message 的 status 用于 return 或 测试
用于 return：
```cpp
return absl::DataLossError("This is a funny error");
```
用于 testing：
```cpp
absl::Status input_status_for_testing = absl::DataLossError("This is a funny error");
...
```
古法（现在别这么用了）：
```cpp
absl::Status input_status_for_testing = 
    absl::Status(absl::StatusCode::kDataLoss, "This is a funny error");
```
