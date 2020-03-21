# Overloading Operators

```cpp
class Receipt {
    int receipt_id;
    float amount;
    
  public:
    // ...
    
    float getAmount();
    
    // Overloading operator +
    float operator + (Receipt receipt) {
        return this->getAmount() + receipt.getAmount();
    }
};
```

```cpp
Receipt r1(10002, 82.5);
Receipt r2(10005, 50.1);

float sum_amount = r1 + r2; // 132.6
```
