# Return Macros

## 用于 非 test 的 code

### CHECK 系列
* 如果 fail，会 break code

### RETURN 系列

#### RETURN_IF_ERROR
```cpp
RETURN_IF_ERROR(status);
```
Log error if error:
```cpp
RETURN_IF_ERROR(status).LogError();
```

Log some custom error message if error:
```cpp
RETURN_IF_ERROR(status).LogError() << "Something I " << "want to say yeah.";
```


### RET_CHECK 系列
* 如果 fail，会 return 一个 `absl::Status` with code `absl::StatusCode::kInternal`，不会 break code
* 可用于 以下的 返回类型的函数内部:
  * `absl::Status`
  * `absl::StatusOr<...>`
  
#### RET_CHECK
```cpp
RET_CHECK(bool)
```
#### RET_CHECK_OK
```cpp
RET_CHECK_OK(status)
```

#### RET_CHECK_EQ
```cpp
RET_CHECK_EA (a, b)
```


### ASSIGN_OR_RETURN
* 如果 fail，会 return failing status。否则 会 assign value 给指定的 variable
* 可用于 以下的 返回类型的函数内部:
  * `absl::Status`
  * `absl::StatusOr<...>`
 
* 一般的用法：
  ```cpp
  ASSIGN_OR_RETURN(auto foo, GetFoo(...));
  foo.DoSomething();
  ```
* 如果要在 fail 的时候，在 error status 的 error message **后面 append** 一段 自定义的 string，用 `_.SetPrepend() << ` (it seems in the latest code standard, we don't need to use SetPrepend any more?)：
  ```cpp
  ASSIGN_OR_RETURN(auto foo, GetFoo(bar), 
                   _.SetPrepend() << "Failed to get Foo for Bar: " << bar);
  ```
  
* 如果要在 fail 的时候，在 error status 的 error message 后面 append 一段 自定义的 string，然后再把原 error status 也 log 出来，用 `_.LogError() << `：
  ```cpp
  ASSIGN_OR_RETURN(auto foo, GetFoo(bar), 
                   _.LogError() << "Failed to get Foo for Bar: " << bar << ", error status: ");
  ```
  
  * There is also `_.LogWarning() << ...`
  
## 用于 tests

### EXPECT 系列
* 如果 fail，test 还会继续进行下去
* **只要有可能，尽量都用 `EXPECT_THAT`。** 因为一旦 test fail，`EXPECT_THAT` 所能提供的 报错信息和分析是最详尽的。

#### EXPECT_THAT
`EXPECT_THAT`优于 `EXPECT` 家族中的所有其他类别，比如 `EXPECT_EQ`, `EXPECT_TRUE`... 

* 替代 `EXPECT_TRUE(...)`
  ```cpp
  // 这样好
  EXPECT_THAT(container1, IsEmpty());
  EXPECT_THAT(container2, Not(IsEmpty()));
    
  // 这样不好
  EXPECT_TRUE(container1.empty());
  ```
* 替代 `EXPECT_EQ(...)`
  ```cpp
  // 这样好
  EXPECT_THAT(container1, SizeIs(5));
  
  // 这样不好
  EXPECT_EQ(container1.size(), 5);
  ```
    
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

#### EXPECT_DEATH
* EXPECT_DEATH 是比较 expensive 的一个语句，会让 test 变慢很多，在 test 里面能不用就不用。
* 如果要测 `CHECK(...)` 的 failure，就用 EXPECT_DEATH:
  ```cpp
  EXPECT_DEATH(SomeFunction(some_invalid_input), "");  // 最后的 "" 应该是放 expected error message 的地方
  ```

### ASSERT 系列
* 如果 fail，会 break test
  * 比如说 create directory，读写文件 等

#### ASSERT_OK_AND_ASSIGN
* `ASSERT_OK_AND_ASSIGN` is a test counterpart of `ASSIGN_OR_RETURN`.
  * 如果 fail，这个 macro 不会 return error status，它会生成一个 test failure，然后 returns (void) from the current function, which must (also) have a void return type.


