# Constructors, Assignment Operators, Destructor, Rule of 3 and Rule of 5

## Constructor
### 一般的 Constructor

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

### Copy Constructor
```cpp
Class(const Class& obj);
```  
Copy Constructor 的样子如上。

一个关于 copy constructor 的很好的 短视频教程（这个视频的前1/3是讲copy，后1/2是讲copy constructor）：https://www.youtube.com/watch?v=BvR1Pgzzr38&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=45

### Move Constructor
```cpp
Class(Class&& obj);
```
Move Constructor 的样子如上。
* 上面的 `&&` 的意思是 RValue Reference
* 上面的 `(...)` 里不是 `const Class&& obj`，是因为 **move 操作 会把 input object 变成 null！这一点要特别注意**

Move Constructor 的目的是 **偷窃或者说挪用 他者 正在拥有的 allocated memory**，所以就不必再 allocate 一遍 memory。这样就：
* 节约了space
* 避免了对各种东西进行copy的时间消耗
* 之后在 run destructor 的时候，也不必 de-allocate 2次memory，而只用 de-allocate 一次

被挪用的 他者 是某个RValue，比如说某个 temporary variable。
Move Constructor 和 RValue Reference 紧密相关，可以参考我关于 RValue Reference 的 note。

Move Constructor 的 样子和 Copy Constructor 很像：
```cpp
// Copy Construcor
Person(const Person & other) {
    ...
}

// Move Constructor
Person(Person && other) { // The input param is a RValue Reference
    ...
}
```

## Assignment Operators
Copy Assignment Operator 和 Move Assignment Operator 都是 overload assignment operator (即`=`).

### Copy Assignment Operator
```cpp
Class& operator = (const Class& obj);
```
Copy Assignment Operator 的样子如上.


### Move Assignment Operator
```cpp
Class& operator = (Class&& obj);
```
Move Assignment Operator 的样子如上。
* 上面的 `&&` 的意思是 RValue Reference
* 上面的 `(...)` 里不是 `const Class&& obj`，是因为 **move 操作 会把 input object 变成 null！这一点要特别注意**


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

## Rule of Three in Class Definition

如果要定义以下三者其中任一个，则需要把这3个都定义了：
* Destructor
  ```cpp
  ~Class();
  ```
* Copy Constructor
  ```cpp
  Class(const Class& obj);
  ```
* Copy Assignment Operator
  ```cpp
  Class& operator = (const Class& obj);
  ```

## Rule of Five in Class Definition
With `move` semantics, the "Rule of 3" becomes "Rule of 5", 就是说除了上面的3个，还需要下面的2个：
* Move Constructor
  ```cpp
  Class(Class&& obj);
  ```
* Move Assignment Operator
  ```cpp
  Class& operator = (Class&& obj);
  ```
