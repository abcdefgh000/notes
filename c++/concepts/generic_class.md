# Generic Class

**In a Generic Class, ALL the member functions must be treated as generic functions.**
We have to add the `template<class T>` to each member function.

```cpp
// Tell compiler this class uses a generic type.
template <class T>
class StudentRecord
{
  private:
    const int size = 5;
    T grade;
    int studentId;
  public:
    StudentRecord(T input);
    void setId(int idIn);
    void printGrades();
};

template<class T>
StudentRecord<T>::StudentRecord(T input)
{
    grade=input;
}

// Still add the `template<class T>` here,
// even though this function does not touch any generic type!
template<class T>
void StudentRecord<T>::setId(int idIn)
{
    studentId = idIn;
}

template<class T>
void StudentRecord<T>::printGrades()
{
    cout<<"ID# "<<studentId<<": ";
    cout<<grade<<"\n ";
    cout<<"\n";
}

template<class T>
void StudentRecord<T>::setId(int idIn)
{
    studentId = idIn;
}

template<class T>
void StudentRecord<T>::printGrades()
{
    cout<<"ID# "<<studentId<<": ";
    cout<<grade<<"\n ";
    cout<<"\n";
}
```
