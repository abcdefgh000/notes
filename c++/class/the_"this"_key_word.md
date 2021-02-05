# The `this` key word in C++ class

一个很好的关于 `this` key word 的短视频教程：https://www.youtube.com/watch?v=Z_hPJ_EhceI&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=42

`this` is a pointer to the current object instance that the (non-static) member methods belongs to.

在一个 member function 里，`this` 是一个 pointer that cannot be redirected:
```cpp
class GameObject {
 public:
  int x, y;
  
  SetLocation(int x, int y) {
    this->x = x;  // `this` is a `GameObject* const`
    this->y = y;
  }
}
```

更特殊的情况下：在一个 const member function 里，`this` 是一个 pointer that cannot be redirected, and also the content that this pointer points to cannot be modified:
```cpp
class GameObject {
 public:
  int x, y;
  
  GetLocation(int x, int y) const {
    std::cout << this->x << ", " << this->y << std::endl;  // `this` is a `const GameObject* const`
  }
}
```

