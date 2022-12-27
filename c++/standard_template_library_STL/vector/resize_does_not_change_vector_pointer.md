# How to make sure `resize()` doesn't change the pointer of the vector

Thanks to `Xiaojie Hao` for this knowledge.

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

template<class T>
void CustomVector<T>::reserve(int reserve_size) {
  if (reserve_size <= storage_footprint_) {
    return;
  }
  
  T* new_pointer_to_elements = new T[reserve_size];
  for (int i = 0; i < size_; ++i) {
    new_pointer_to_elements[i] = elements_[i];
  }
  
  delete[] elements_;
  elements_ = new_pointer_to_elements;
  
  storage_footprint_ = reserve_size;
}
```

So we can make sure that, for example in the following case, after a vector is resized, the pointer that pointed to the vector object before the resizing happened can still access the (elements of the) vector correctly, since the pointer of the vector never changed after the resizing:

```cpp
std::vector<int> my_vector = { 100 };

std::vector<int>* ptr_to_vector = &my_vector;

// Assume a resize is happening here
my_vector.push_back(200);

// We can still use `ptr_to_vector` just as we did before the resize happened.
```

because according to the above design of the `class CustomVector`, the pointer to the vector object never need to be changed after a resizing.
