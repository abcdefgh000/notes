# Functor

给一个 Class 搞一个 Operator Overload for the "function call operator `()`"，这个 Class 就变成了一个所谓的 `Functor`. 然后就可以 create an object of this Class and **this object can operate as if it were a function**.

To use a functor, we need to:
* First, instantiate a functor instance of the Functor Class
* Second, call the functor by this syntax:
  ```cpp
  functor_instance_name(input_param);
  ```

举例代码:
```cpp
#include <algorithm> // For `transform`
#include <iostream>
#include <vector>

// A Functor
class Increment {
 private:
  int increment_amount_;
  
 public:
  Increment(int inc) : increment_amount_(inc) {}
  int GetIncrementAmount() const { return increment_amount_; }
  
  // This operator overloading enables calling `()` on objects of this Class
  int operator () (int num) const {
    return num + increment_amount_;
  }
};

// Using this Functor
int main() {
  std::vector<int> numbers = {1, 2, 3};
  
  // Instantiate a Functor of Class `Increment`.
  Increment incre(10);
  std::cout << "The increment amount is: " << incre.GetIncrementAmount() << std::endl; // 10
  
  // Using the above Functor directly.
  int result = incre(25);
  std::cout << "25 increased by " << incre.GetIncrementAmount() << " is:" << result << std::endl; // 35
  
  // Using this Functor as a parameter of the `transform`.
  transform(numbers.begin(), numbers.end(), numbers.begin(), Increment(100));
  
  for (int num : numbers) {
    std::cout << num << " "; // 101 102 103
  }
}

```


## Reference
* https://www.geeksforgeeks.org/functors-in-cpp/
