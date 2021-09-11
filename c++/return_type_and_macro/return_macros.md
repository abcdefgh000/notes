# return macros

## CHECK 系列
* 如果 fail，会 break code

## ASSERT 系列
* 如果 fail，会 break code

## RET_CHECK 系列
* Returns `Status`
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
