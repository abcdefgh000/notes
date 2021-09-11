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
* **只要有可能，尽量都用 `EXPECT_THAT`！** 因为一旦 test fail，`EXPECT_THAT` 所能提供的 报错信息和分析是最详尽的！
  * `EXPECT_THAT`优于 `EXPECT` 家族中的所有其他类别，比如 `EXPECT_EQ`, `EXPECT_TRUE`... 
  * `EXPECT_THAT` 也可取代 `ASSERT_OK_AND_ASSIGN`，举例：
    ```cpp
    // 这样写是最好的
    absl::StatusOr<xxx> GetSomething(...) {
      ...
    }
    EXPECT_THAT(GetSomething(...), IsOkAndHolds("expected_foo_value"));
    
    // 下面这样写就没那么好
    ASSERT_OK_AND_ASSIGN(auto foo, GetSomething(...));
    EXPECT_EQ(foo, "expected_foo_value");
    ```

## ASSERT 系列 (用于 tests）
* 如果 fail，会 break test


