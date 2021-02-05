# Overloading "<<" for cout printing

在 `cout << obj` 里，`<<`的左边是 `cout`，右边是 `obj`。但我们如果要把 `<<` overload 成 class of obj 里的一个member function 的话，所有的 class member function的第一个parameter都必须（隐式地）是 这个class object 的 `this` pointer，而不可以作为第二个 parameter 出现在 function的parameter list 里，所以`<<`无法被 overload 成一个 member function。所以：

1. 它如果要呆在 class 里，就只能是一个 friend function，必须 显示地 含有 `obj` 作为第二个 param，并且弄一个 `ostream` 作为第一个 param，如下：
```cpp
#include <iostream>
#include <string>

using namespace std;

class Person {
  private:
    string name;
    int age;

  public:
    Person(string name, int age) : name(name), age(age) {}

    // We cannot and don't need to put a `const` before the `{`,
    // since this function is not a member function.
    // 如果把 `friend` 去掉，compiler会报错，因为compiler会认为本函数是一个 member function，所以
    // compiler会认为本函数还有一个隐含的输入参数 `this`，但 operator << 的 overload 只能有2个参数，
    // 所以 compile 不会通过。
    friend ostream & operator << (ostream & outStream, const Person & person) {
        outStream << person.name << ", " << person.age << endl;
        return outStream;
    }
};

int main() {
    Person person("Dick", 100);
    cout << person; // "Dick, 100"
    return 0;
}
```

2. 如果把这个 overload operator << 函数 放到 class的外面，则如此：
```cpp
class Person {
  private:
    string name;
    int age;

  public:
    Person(string name, int age) : name(name), age(age) {}

    string getName() const { return this->name; }
    int getAge() const { return this->age; }
};

ostream & operator << (ostream & outStream, const Person & person) {
    outStream << person.getName() << ", " << person.getAge() << endl;
    return outStream;
}
```

因为原版的 `<<` 会返回一个 `ostream`（因此我们才能 chain 一串 `cout << a << b;`），所以 我们 overload 的 `<<` 也必须return 一个 ostream。

