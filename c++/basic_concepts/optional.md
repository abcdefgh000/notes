# Optional

```cpp
#include <optional>

std::optional<std::string> MaybeReturnAString(int student_id) {
  std::string student_name;
  ...
  
  if (this_student_id_exists) {
    return student_name;
  }
  
  // This `{}` is to return an empty std::optional!
  return {};
}


```
