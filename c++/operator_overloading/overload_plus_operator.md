# Overloading Plus (+) Operator

## 作为 member function，只接受一个param 即 +号右边的param
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

    Food operator + (const Food & other) {
        string name = this->getName() + ", " + other.getName();
        double weight = this->getWeight() + other.getWeight();
        Food foodSum(name, weight);
        return foodSum;
    }
};

int main() {
    Food apple("Apple", 1);
    Food cake("Cake", 1.5);
    Food foodSum = apple + cake;
    cout << foodSum.getName() << ": " << foodSum.getWeight() << '\n';
    return 0;
}
```

## 作为 class 以外的 独立 function，接受2个param，即 +号两边的2个param
### 2个param都是 本class的object
```cpp
class Food {
  // ...
};

Food operator + (const Food & food1, const Food & food2) {
    string name = food1.getName() + ", " + food2.getName();
    double weight = food1.getWeight() + food2.getWeight();
    Food foodSum(name, weight);
    return foodSum;
}
```

### 2个param的data type 不同
```cpp

```

### 返回值也可以不是 这个 class 的 type
```cpp

```
