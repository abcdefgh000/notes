```cpp
std::vector<int> RepeatedFieldToIntVector(
    const proto2::RepeatedField<int>& repeated_int_field) {
  std::vector<int> int_vector(repeated_int_field.begin(), repeated_int_field.end());
  return int_vector;
}
```
