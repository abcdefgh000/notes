# Use Custom Class Object as Map Key

要点：
* 要用 custom class object 来做 map key，就 **必须让这个 class 是 comparable 的**，
  * 因为：
    * map 必须能比较 任意2个key 是否相等
    * C++ 里的 `map` class 还会自动地动态地 排序所有的 keys
  * 要实现keys的可比较，在C++里是通过 **overload operator `<`** 来实现的，示例code如下：
    ```cpp
    bool operator < (const Person &other) const {
        if (name == other.name) {
            return age < other.age;
        }
        return name < other.name;
    }
    ```
  * 注意！如果 overloaded operator `<` 不涵盖我们的 custom class的所有 member fields的话，那么就会出现这种情况：2个不完全相同的instances被map认为是相同的key。这个情况未必是错的，要看我们的需求。 
  * 题外话：对于 operator `<`，这么一个statement：`bool isSmaller = obj1 < obj2`，我们可以这么理解
    * **`<` 是 `obj1` 的一个 member function，`obj2` 是这个function的输入参数，`bool isSmaller` 是这个function的 返回值**

* The member function `void print()` of class `Person` **must be `void print() const`!**
  * Since in the `main` function when we call `it->first.print();`, the `it->first` returns a **`const`** instance of the `Person` class, so any function called by this const instance must be a const member function, since this const instance refuses any potential changes.
  * It is also a good practice to make the member functions that are not supposed to change the class object to be a const member function.

```cpp
#include <iostream>
#include <map>
#include <string>

using namespace std;

class Person {
  private:
    string name;
    int age;

  public:
    Person(string name, int age) :
        name(name), age(age) {}

    void print() const {
        cout << name << " - " << age << flush;
    }

    // Overload the operator `<`, we have to do this if we want to use this class as
    // keys in a map.
    bool operator < (const Person &other) const {
        if (name == other.name) {
            return age < other.age;
        }
        return name < other.name;
    }
};

int main() {
    map<Person, int> people;

    people[Person("Mike", 40)] = 40;
    people[Person("Sue", 30)] = 30;
    people[Person("Raj", 40)] = 20;

    for (map<Person, int>::iterator it = people.begin(); it != people.end(); it++) {
        cout << "key: " << it->second << ", value: ";
        it->first.print();
        cout << endl;
    }
    return 0;
}
```
