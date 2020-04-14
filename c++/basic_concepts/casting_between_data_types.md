# Casting between Data Types

## Static Casting
### Static Casting 是最基本，也是最常用的cast 方式
```cpp
double num = 2.9;
int intNum = static_cast<int>(num); // 2
```

### Static Casting 用于 parent and sub class
```ccp
class Shape {};

class Rectangle : public Shape {};

int main() {
    Shape shape;
    
    // 下面这个不合法！
    Rectangle * pRectangle = &shape;
    
    // Static Cast 成一个 指向 Rectangle 型 object 的 指针
    Rectangle * pRectangle = static_cast<Rectangle *>(&shape);

    return 0;
}
```

### 用 Static Cast 把 LValue 转为 RValue Reference
```cpp
Student student; // LValue.
Student && pStudent = static_cast<Student &&>(student);
```

## Dynamic Casting
Static Casting 会强行cast，直到在 run time 出错。Dynamic Casting 在遇到不合理的casting的时候，会返回 nullptr。比如 如果我们要从子类cast到
父类，static casting会强行照做，但 dynamic casting 会返回 nullptr。
```cpp
class Shape {};

class Rectangle : public Shape {};

int main() {
    Shape shape;
    Rectangle * pRectangle = dynamic_cast<Rectangle *>(&shape);
    if (pRectangle == nullptr) {
        cout << "Invalid casting" << endl;
    }
    cout << pRectangle << endl;
    
    return 0;
}
```

