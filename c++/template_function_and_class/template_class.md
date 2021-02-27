# Template Class

**In a Template Class, ALL the member functions must be written as template functions, no matter that function did has any template stuff in it or not.**
We have to add the `template<class T>` to each member function.

```cpp
// Tell compiler this class uses a template type.
template <class T>
class StudentRecord {
  private:
    const int size = 5;
    T grade;
    int studentId;
  public:
    StudentRecord(T input_grade);
    void setId(int idIn);
};

template<class T>
StudentRecord<T>::StudentRecord(T input_grade) {
    grade = input_grade;
}

// Still add the `template<class T>` here,
// even though this function does not touch any template type!
template<class T>
void StudentRecord<T>::setId(int idIn) {
    studentId = idIn;
}

template<class T>
void StudentRecord<T>::printGrades() {
    cout<<"ID# "<<studentId<<": ";
    cout<<grade<<"\n ";
    cout<<"\n";
}

template<class T>
void StudentRecord<T>::setId(int idIn) {
    studentId = idIn;
}
```

To instantiae an object of the above Template Class:
```cpp
StudentRecord<int> student1(98);
StudentRecord<float> student2(99.5);

...
```

## 一个 template class 里，既有 typename 参数，又有 primitive type 参数的情况：
```cpp
template<typename T, int size>
class CustomArray {
 private:
  T internal_array_[size];
 public:
  int GetSize() const { return size; }
};

int main() {
  CustomArray<int, 5> custom_array;
  std::cout << custom_array.GetSize() << std::endl;  // 5
}
```

