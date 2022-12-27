# How to make sure `resize()` doesn't change the pointer of the vector

The trick is:

Create a private field `elements_` (which itself is a pointer) in the vector object, use `elements_` to hold the elements in the vector, so as long as we have the pointer (address) to the vector object, we will have the pointer (address) to the `elements_` field.

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

So when we do `resize()`, we should not change the pointer to the vector object, and we should not change the pointer to the `elements_` field, we just change the address that `elements_` (which is a pointer field) points to:

```cpp
template<class T>
void CustomVector<T>::resize(int new_size) {
  // The major tricks are done inside here!
  reserve(new_size);
  
  for (int i = size_; i < new_size; ++i) {
    elements_[i] = T();
  }
  
  size_ = new_size;
}
```
