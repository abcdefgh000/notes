# return macros

## CHECK 系列 (用于 非 test 的 code)
* 如果 fail，会 break code

## RET_CHECK 系列 (用于 非 test 的 code)
* 如果 fail，会 return 一个 `absl::Status` with code `absl::StatusCode::kInternal`，不会 break code
* 可用于:
  * `absl::Status`
  * `absl::StatusOr<...>`
### RET_CHECK
```cpp
RET_CHECK(bool)
```
### RET_CHECK_OK
```cpp
RET_CHECK_OK(status)
```

## EXPECT 系列 (用于 tests)
* 如果 fail，test 还会继续进行下去

## ASSERT 系列 (用于 tests）
* 如果 fail，会 break test


