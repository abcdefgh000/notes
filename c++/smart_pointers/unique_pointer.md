# Unique Pointer

* Prefer creating unique pointer with `std::make_unique<MyClass>(obj1)` or `absl::make_unique<MyClass>(obj1)` instead of using `new`
* Prefer using the `=` operator instead of `reset` to reassign the unique pointer

```cpp
{
  auto student = std::make_unique<Student>(1001);
  ...
  student->DoSomething();
  ...
  student = std::make_unique<Student>(2001);  // The old Student object is deleted.
  ...
  AnotherFunction(*student);
}  // The Student object is deleted when goes out of scope.
```

如果一个函数的 input argument 是一个 unique pointer，传入这个 unique pointer 的时候，要用 `absl::move(...)` 或者 `std::move(...)`，用absl更好。

特别注意！如果把一个 unique pointer 传入了一个函数，那么之后 caller 就不再own 这个 unique pointer 了！比如下面的code:
```cpp
void FunctionA (...) {
  ...
  auto student = std::make_unique<Student>(1001);
  
  // 1
  
  FunctionB(absl::move(student));
  
  // 2
  ...
}
```
在 `//1` 那里，FunctionA 还 own `student` 这个 unique pointer。但到了 `//2` 以及之后的地方，FunctionA 都不再 own `student` 了！`student` 已经永远归属并沉没到 FunctionB 里面去了。

如果不想传入 unique pointer 并且想特意表达 输入参数”无“ 的时候，可以传入 nullptr：
```cpp
void SomeFunction(std::unique_ptr<SomeClass> something) {
  // ...
}

SomeClass sth = ...;

SomeFunction(some_bool_flag ? absl::make_unique<SomeClass>(sth) : nullptr);
```
