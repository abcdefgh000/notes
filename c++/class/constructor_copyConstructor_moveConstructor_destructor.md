# Constructor, Copy Constructor, Move Constructor, Destructor, Rule of 3 and Rule of 5

关于 copy operator 和 assignment operator，在别的笔记里记录。这里只记录 copy constructor 和 move constructor。

## Constructor
Constructor is special class function that is executed **automatically** whenever we create a new instance of the class.

Constructor does not return anything, including void.

```cpp
class ClassName
{
    // ...
  public:
    ClassName();
    ClassName(// parameters);
    ...
};

ClassName::ClassName()
{
   // do sth
}

ClassName::ClassName(// parameters)
{
   // do sth 
}
```

## Copy Constructor
一个关于 copy constructor 的很好的 短视频教程（这个视频的前1/3是讲copy，后2/3是讲copy constructor）：https://www.youtube.com/watch?v=BvR1Pgzzr38&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=45

## Move Constructor



## Destructor
Destructor is a special class functions that is called **automatically** whenever **an object goes out of scope**, like when a `}` is met.

Destructor cannot return anything, or accept any parameters.

Destructor is releasing memory that was allocated by the class constructor and member functions.

```cpp
class ClassName
{
    // ...
  public:
    // ...
    ~ClassName();
};

ClassName::~ClassName()
{
    // do sth
}
```
