# Standard Template Library (STL)

## Copy between containers
比如，copy 一个 vector 里的所有东西 到一个 set 里去：
```cpp
absl::flat_hash_set<std::string> example_set(example_vector.begin(), example_vector.end());
```
