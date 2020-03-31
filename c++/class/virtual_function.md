# Virtual Function

## Virtual Function with implementation
```cpp
/* header file for main.cpp
*/ 

#include<iostream>
#include<string>
using namespace std;

//Employee is a class for calculating the
//pay for an hourly employee. 
class Employee
{
    protected:
        float payRate;
        string name;
        int employeeNumber;
    public:
        void setPayRate(float rateIn);
        float getPayRate();
        //This is now a virtual function
        virtual float calcWeeklyPay() {
            return 40 * payRate;
        }
};
void Employee::setPayRate(float rateIn)
{
    payRate = rateIn;
}
float Employee::getPayRate()
{
    return payRate;
}

//The class manager inherits from Employee
//The only difference... managers are salary
//employees. So the pay is calculated differently.
class Manager : public Employee
{
    public:
        float calcWeeklyPay() {
            return payRate / 52;
        }
};
```

## Pure Virtual Function with no implementation
```cpp
//header file for main.cpp

#include<iostream>
#include<string>

using namespace std;

class Animal {
    private:
        string name;
        float baseRate;
        string type;
    public:
        Animal(string nameIn, float baseRateIn, string typeIn);
        //this is our virtual function
        virtual float calcDailyRate() = 0;
        float getBaseRate();
};

Animal::Animal(string nameIn, float baseRateIn, string typeIn) {
    name = nameIn;
    baseRate = baseRateIn;
    type = typeIn;
}

float Animal::getBaseRate()
{
   return baseRate; 
}

class Cat: public Animal
{
        public:
        Cat(string nameIn, float baseRateIn, string typeIn);
        float calcDailyRate();
};

Cat::Cat(string nameIn, float baseRateIn, string typeIn)
        :Animal(nameIn, baseRateIn, typeIn)
        {
            cout<<"\nin cat constructor";
        }

float Cat::calcDailyRate()
{
    return Animal::getBaseRate() * 1.5;
}

class Dog: public Animal
{
        public:
        Dog(string nameIn, float baseRateIn, string typeIn);
        float calcDailyRate();
};

Dog::Dog(string nameIn, float baseRateIn, string typeIn)
        :Animal(nameIn, baseRateIn, typeIn)
        {
            cout<<"\nin dog constructor";
        }

float Dog::calcDailyRate()
{
    return Animal::getBaseRate() * 2.0;
}
```

