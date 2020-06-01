# Unique Pointer

* Prefer creating unique pointer with `std::make_unique` instead of using `new`
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
