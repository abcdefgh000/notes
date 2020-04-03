# Overloading Plus (+) Operator

## 作为 member function
```cpp
```

## 作为 class 以外的 独立 function
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

