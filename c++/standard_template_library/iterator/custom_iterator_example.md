# A Custom Iterator Example

## Custom Vector and Custom Iterator
```cpp
#include <iostream>
#include <vector>

using namespace std;

class CustomVector {
  private:
	vector<int> data;

  public:
    // 特别注意！必须把 custom iterator 定义为 custom vector 的 附属class，才能
    // 使用 CustomVector::CustomIterator 来初始化一个 custom iterator 的 instance!
	class CustomIterator {
	private:
		int pos;
		CustomVector & customVector;

	public:
		CustomIterator(int pos, CustomVector & customVector) :
				pos(pos), customVector(customVector) {}

		// Overloading the "Post ++" operator, for like "iterator++".
		// Return a copy of the original iterator.
		CustomIterator operator ++ (int) {
			// Make a copy of the original iterator.
			CustomIterator originalIterator = *this;
			++pos;
			return originalIterator;
		}

		// Overloading the "Prefix ++" operator, for like "++iterator".
		// Return the reference of the iterator.
		CustomIterator & operator ++ () {
			++pos;
			return *this;
		}

		// Overloading the "*" operator, for like "*iterator".
		// 注意！下面这个 `*customIterator` 和 `class CustomIterator` 内部的 `*this` 是
		// 完全不同的两种东西！
		int operator * () {
			return customVector.get(pos);
		}

		bool operator == (const CustomIterator & other) const {
			return pos == other.pos;
		}

		bool operator != (const CustomIterator & other) const {
			return pos != other.pos;
		}
	};

	CustomVector() {}

	~CustomVector() {}

    // Get the size of the internal vector.
	int size() {
		return data.size();
	}

    // 用于 customIterator = customVector.begin();
	CustomIterator begin() {
		return CustomIterator(0, *this);
	}

    // 用于 customIterator != customVector.end();
	CustomIterator end() {
		return CustomIterator(this->size(), *this);
	}

	void add(int value) {
		data.push_back(value);
	}

	int get(int pos) {
		if (pos < 0 || pos >= this->size()) {
			cout << "Invalid position: " << pos << endl;
			return INT_MIN;
		}
		return data[pos];
	}
};
```

## Main function
```cpp
#include <iostream>
#include <vector>
#include "custom_iterator.h"

using namespace std;

int main() {
    CustomVector customVector;
	customVector.add(10);
	customVector.add(20);
	customVector.add(30);

	cout << customVector.get(0) << endl; // 10
	cout << customVector.get(2) << endl; // 30
	cout << customVector.get(3) << endl; // -2147483648
	cout << customVector.get(-1) << endl; // -2147483648

    for (CustomVector::CustomIterator customIterator = customVector.begin();
	        customIterator != customVector.end(); customIterator++) {
        cout << *customIterator << endl;
	}

    return 0;
}
```
