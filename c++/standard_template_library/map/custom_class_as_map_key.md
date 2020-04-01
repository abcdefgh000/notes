# Use Custom Class Object as Map Key

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

	Person() :
			name(""), age(0) {

	}

	Person(string name, int age) :
			name(name), age(age) {

	}

	Person(const Person& other) {
		name = other.name;
		age = other.age;
	}

	void print() const {
		cout << name << ": " << age << flush;
	}

	bool operator<(const Person &other) const {

		if (name == other.name) {
			return age < other.age;
		} else {
			return name < other.name;
		}
	}
};
```
