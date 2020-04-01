# Map in C++ Overview

## Create a map, add items into a map
```cpp
map<string, int> ages;

ages["Mike"] = 40;
ages["Raj"] = 20;
ages["Vicky"] = 30;
```

### Create a pair and insert a pair into a map
```cpp
ages.insert(make_pair("Peter", 100));
```

## Search an item in a map
```cpp
if(ages.find("Vicky") != ages.end()) {
    cout << "Found Vicky" << endl;
} else {
    cout << "Key not found." << endl;
}
```

## Loop the elements in a map

### Loop by iterator
```cpp
for(map<string, int>::iterator it = ages.begin(); it != ages.end(); it++) {
    cout << it->first << ": " << it->second << endl;
}
```
**注意！** 用`it->first` 得到的 key 是 **`const`** key！是不可以被modify的！

### Loop by iterator and Pair
```cpp
for(map<string, int>::iterator it = ages.begin(); it != ages.end(); it++) {
    // Use `*it` to get the `pair`.
    pair<string, int> age = *it;
    // For `pair`, use `.first` instead of `->first`.
    cout << age.first << ": " << age.second << endl;
}
```

### Loop by `:` and Pair
```cpp
for (pair<Person, int> pair : people) {
    cout << "key: " << pair.second << ", value: ";
    pair.first.print();
    cout << endl;
}
```
or use `auto` to replace the data type of `pair`:
```cpp
for (auto pair : people) {
    ...
}
```

