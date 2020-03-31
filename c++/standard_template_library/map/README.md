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

### Loop by Pair
```cpp
for(map<string, int>::iterator it = ages.begin(); it != ages.end(); it++) {
    pair<string, int> age = *it;
    cout << age.first << ": " << age.second << endl;
}
```

