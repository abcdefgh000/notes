# Unique Pointer

```cpp
#include <iostream>
#include <memory> // Needed for using unique pointer.

using namespace std;

class Test {
  public:
    Test() {
        cout << "created" << endl;
    }

    void greet() {
        cout << "Hello" << endl;
    }

    ~Test() {
        cout << "destroyed" << endl;
    }
};

int main() {
    unique_ptr<Test[]> pTest(new Test[2]);
    pTest[1].greet();

    cout << "Finished" << endl;
    return 0;
}
```

The output of the above code is:
```
created
created
Hello
Finished
destroyed
destroyed
```
