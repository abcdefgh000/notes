# Custom Vector Data Type that is Circular, Iterable and Works with Template Types

```cpp
//ring.h

#pragma once
#include <vector>

// Note that this implementation of the ring class was written by
// Paul T (DeveloperPaul123@github)
template <typename T>
class ring {
    std::vector<T> _data;
    int _cur_index;

  public:
    class iterator;
   
    ring(int size) : _cur_index(0) {
        _data.reserve(size);
        for(auto i = 0; i < size; i++) {
            _data.push_back(T());
        }
    }

    void add(T value) {
        if (_cur_index < _data.size()) {
            _data[_cur_index] = value;
            _cur_index++;
        } else {
            _cur_index = 0;
            _data[_cur_index] = value;
        }
    }

    T get(int index) {
        if (index >= 0 && index < _data.size()) {
            return _data[index];
        }
        return T();
    }

    int size() {
        return static_cast<int>(_data.size());
    }	
};

// The iterator class of the ring class.
// 注意！ring<T>::iterator 这里要带个 <T> ！
template<typename T>
class ring<T>::iterator {
  public:
    void print() const;
};

template<typename T>
void ring<T>::iterator::print() const {
    std::cout << "Hello from iterator." << std::endl;
}
```

```cpp
//============================================================================
// Name        : NestedTemplateClasses.cpp
// Author      : John Purcell
// Version     :
// Copyright   : Your copyright notice
// Description : Nested Template classes
//============================================================================

#include <iostream>
#include <string>
#include "ring.h"

using namespace std;

int main() {
	ring<string>::iterator it;
	it.print();

	ring<string> textRing(3);
	
	textRing.add("one");
	textRing.add("two");
	textRing.add("three");
	textRing.add("four");


	for(auto i =0; i < textRing.size(); i++)
	{
		cout << textRing.get(i) << endl;
	}

	return 0;
}
```
