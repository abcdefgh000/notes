# Constructor and Destructor

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
