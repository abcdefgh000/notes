# Generic Class

**In a Generic Class, ALL the member functions must be written as generic functions, no matter that function did has any generic stuff in it or not.**
We have to add the `template<class T>` to each member function.

```cpp
// Tell compiler this class uses a generic type.
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
// even though this function does not touch any generic type!
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

## Instantiae a Generic Class
```cpp
StudentRecord<int> student1(98);
StudentRecord<float> student2(99.5);

...
```
