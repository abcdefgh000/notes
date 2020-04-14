# Casting between Data Types

## Static Casting
Static Casting 是最基本，也是最常用的cast 方式。
```cpp
double num = 2.9;
int intNum = static_cast<int>(num); // 2
```

Static Casting 用于 parent and sub class 的例子：
```ccp
class Shape {};

class Rectangle : public Shape {};

int main() {
    Shape shape;
    
    // 下面这个不合法！
    Rectangle * pRec = &shape;
    
    // Static Cast 成一个 指向 Rectangle 型 object 的 指针
    Rectangle * pRec = static_cast<Rectangle *>(&shape);

    return 0;
}
```
