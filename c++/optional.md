# Optional

```cpp
#include <optional>

std::optional<std::string> MaybeReturnStudentName(int student_id) {
  std::string student_name;
  ...
  
  if (this_student_id_exists) {
    return student_name;
  }
  
  // This `{}` is to return an empty std::optional!
  return {};
}

int main() {
  int student_id = 48;
  std::optional<std::string> maybe_student_name = MaybeReturnStudentName(student_id);
  
  // 这里也可以直接用 if (maybe_student_name)
  if (maybe_student_name.has_value()) {
    // 这里也可以直接用 *maybe_student_name，这样 optional 的用法就像一个 pointer
    std::cout << "We got a student name " << maybe_student_name.value() << " for the student id " << student_id;
  } else {
    std::cout << "No student name associated with student id " << student_id;
  }
}
```

继续上面的例子，举另外一种例子：
```cpp
std::string result = maybe_student_name.value_or("Got no name!");
```
上面这样的做法，就是设一个默认的返回值，如果 optional 没有get任何东西，就返回这个 默认值。
