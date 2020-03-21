# Overloading Operators

```cpp
class Receipt {
    int receipt_id;
    float amount;
    
  public:
    // ...
    
    float getAmount();
    
    // Overloading operator +
    int operator + (Receipt receipt) {
        return this->getAmount() + receipt.getAmount();
    }
};
```
