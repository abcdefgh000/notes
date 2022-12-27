# How to make sure `resize()` doesn't change the pointer of the vector

The trick is:
1. Create a private field `elements_` in the vector object, use `elements_` to hold the elements in the vector, so the pointer to the vector object is independent from the pointer of the elements
