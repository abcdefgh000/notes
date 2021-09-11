# Status and StatusOr


## 判断一个 error status 的 error type
### 在 非 test code 里的 判断方法
比如，判断一个 status 是否是 `NOT_FOUND` Error：
```cpp
auto status = ...
if (absl::IsNotFound(status)) {
  ...
}
```
别这么用（在 test 里才用到这种 enum，见下文）：
```cpp
status.code() == absl::StatusCode::kDataLoss
```

### 在 test code 里的 判断方法
在 test 里不仅能判断 error type，还能判断 error message 的 substring：
```cpp
EXPECT_THAT(SomeFunctionThatReturnsStatus(...),
            StatusIs(absl::StatusCode::kInternal, HasSubstr("error message sub string")));

```


## 判断 StatusOr 是否是 ok
直接用：
```cpp
absl::StatusOr<xxx> foo = ...
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

## 取 StatusOr 的 value
用：
```cpp
absl::StatusOr<xxx> foo = ...
auto value = *foo;
...
```

不要用：
```cpp
foo.value()
```

## Call StatusOr 的 value 的 member function
用 `->`：
```cpp
absl::StatusOr<xxx> foo = ...
if (foo.ok()) {
  foo->DoSomething();
}
```
不要用 下面这两种做法：
```cpp
if (foo.ok()) {
  // 语法累赘
  (*foo).DoSomething();
  // 语法累赘
  foo.value().DoSomethingElse();
}
```



## Create 特定 type 和 error message 的 Status 用于 return 或 测试
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
