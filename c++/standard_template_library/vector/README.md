# Vector in C++ Overview
C++里的 vector 是连续存储的，它的各方面有点像 Java 里的 ArrayList.

Vector 可以用 `vector[i]` 这样来 读，写，或者loop，像 C++里的 array 一样.

## To sort a vector
可以给 sort function 一个range，这个range的起始位置和终止位置都要用 iterator 来表达。通常直接从vector的begin一直sort到end
```cpp
std::sort(vector.begin(), vector.end());
```

### Sort a vector of custom class objects
#### 第一种方法：给 custom class 加一个 overloaded operator `<`
```cpp
bool operator < (const MyClass & other) const {
    return this->field1 < other.field1;
}
```

#### 第二种方法：造一个 comparator function，扔到 sort function 里去
```cpp
bool comparatorFunction(const MyClass & obj1, const MyClass & obj2) {
    return obj1.field1 < obj2.field2;
}
```
