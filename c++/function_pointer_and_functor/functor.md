# Functor

A "Functor" a simply a Class with an Operator Overload for the "function call operator `()`"

举例代码:
```cpp
// A Functor
class Increment {
 private:
  int increment_amount_;
  
 public:
  Increment(int inc) : increment_amount_(inc) {}
  
  // This operator overloading enables calling `()` on objects of this Class
  int operator () (int num) const {
    return num + increment_amount_;
  }
};

// Using this Functor
int main() {
  std::vector<int> numbers = {1, 2, 3};
  
  int increment_amount = 10;
  // Using this Functor as a parameter of the `transform`.
  transform(numbers, numbers + numbers.size(), numbers, inrement(increment_amount));
  
  for (int num : numbers) {
    std::cout << num << " ";
  }
}
```


## Reference
* https://www.geeksforgeeks.org/functors-in-cpp/
