# How to make sure `resize()` doesn't change the pointer of the vector

The trick is:

1. Create a private field `elements_` in the vector object, use `elements_` to hold the elements in the vector, so as long as we have the pointer (address) of the vector object, we will have the pointer (address) of the `elements_` field.

```cpp
template<class T> class CustomVector
{
 public:
  ...
  void resize(int new_size);
  void reserve(int reserve_size);
  ...

 private:
  T* elements_;             // Pointer to the first element of the vector
  int size_;		            // Number of elements in the vector
  int storage_footprint_;   // Total space reserved for the vector, including elements and free space
};
```
