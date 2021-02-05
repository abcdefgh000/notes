# Overloading Equal (==) and Non-Equal (!=) Operator

## 作为 member function
```cpp
#include <iostream>
#include <string>

using namespace std;

class Food {
  private:
    string name;
    double weight;

  public:
    Food(string name, double weight) : name(name), weight(weight) {}
    
    string getName() const { return this->name; }
    double getWeight() const { return this->weight; }

    bool operator == (const Food & other) const {
        return this->name == other.getName() && this->weight == other.getWeight();
    }

    bool operator != (const Food & other) const {
        return this->name != other.getName() || this->weight != other.getWeight();
    }
};

int main() {
    Food apple("Apple", 1);
    Food cake("Cake", 1.5);
    cout << (apple == cake) << '\n'; // 0
	cout << (apple != cake) << '\n'; // 1
    return 0;
}
```

## 作为 non-member function
```cpp
class Food {
    // ...
};

bool operator == (const Food & food1, const Food & food2) {
    return food1.getName() == food2.getName() && food1.getWeight() == food2.getWeight();
}

bool operator != (const Food & food1, const Food & food2) {
    return food1.getName() != food2.getName() || food1.getWeight() != food2.getWeight();
}
```
