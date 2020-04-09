# The "default" and "delete" key word in Object Initialization

## The `default` key word
```cpp
#include <iostream>
#include <string>

using namespace std;

class Student {
    int id = 21001; // default value
    string name = ""; // default value

  public:
    // This means the Constructor with no parameter is using the default implementation.
    Student() = default;
    
    // This means the "Copy Constructor" is using the default implementation.
    Student(const Student & other) = default;
  
    // This means the "Equals Operator" is using the default implementation.
    Student & operator = (const Student & other) = default;

    Student(int id) : id(id) {}
};
```


## The `delete` key word
```cpp
class Student {
    int id = 21001; // default value
    string name = ""; // default value

  public:
    // This means we do not allow any "Copy Constructor".
    Student(const Student & other) = delete;
  
    // This means we do not allow any "Equals Operator".
    Student & operator = (const Student & other) = delete;
};
```

