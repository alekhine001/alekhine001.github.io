
### template ###

템플릿은 함수나 클래스를 개별적으로 다시 작성하지 않아도 여러 자료형으로 사용 할 수 있도록 만들어 놓은 틀입니다. 이는 함수 템플릿과 클래스 템플릿으로 나누어집니다. 비유를 들면 5색 펜

즉 함수를 만들어낼때, 함수의 기능은 명확하지만, 자료형을 모호하게 두는것입니다.

1. 함수템플릿 

```c++
template <typename T>
T function_name(T a, T b){
    //function;
}
```
과 같이 사용합니다.

* '템플릿 특수화' 라고, 특정 자료형에 대해서는 다른 처리를 하고싶을떄 사용합니다. 위 템플릿 선언을 할때의 T를 없애고, 넣고싶은 데이터 타입을 넣으면 됩니다.

```c++
template <class T>
T sum(T a, T b){
   return a + b;
}
 
template<>
char * sum<char*> (char* s1, char* s2){
   char * str= "[char *]문자열은 더할 수 없습니다."; 
   cout << "s1 : " << s1 << endl;
   cout << "s2 : " << s2 << endl;
   return str; 
}
```
2. 클래스 템플릿

함수 템플릿과 유사하게 사용하면 됩니다.

```c++
#include <iostream>
#include <string>
 
using namespace std;
 
template <class T>
class Person{
private:
    string name;
    T height;
public:
    Person(string name, T height):name(name), height(height){}
 
    void printAll(){
        cout << "name : " << name << endl;
        cout << "number : " << height << endl;
    };
 
    void setName(string name){
        this->name = name;
    }
    void setNumber(T height){
        this->height = height;
    }
};
int main() {
//객체를 선언할때 <> 안에 template 의 타입을 넣는다.
    Person<int> p1("Mr. Dev C++", 173);
    Person<string> p2("Ms. Unix", "155cm");
 
    p1.printAll();
    p2.printAll();
    cout << endl;
    p1.setNumber(188);
    p2.setNumber("2m 10cm");
    cout << endl;
    p1.printAll();
    p2.printAll();
    return 0;
}
```

멤버함수가 클래스 외부에서 선언될때도 template 선언을 해주어야 합니다.

```c++
#include <iostream>
#include <string>
 
using namespace std;
 
template <class T>
class Person{
private:
    string name;
    T height;
public:
    Person(string name, T height);
    void printAll();
    void setName(string name);
    void setNumber(T height);
};
 
template <class T>
Person<T>::Person(string name, T height):name(name), height(height){}
 
template <class T>
void Person<T>::printAll(){
    cout << "name : " << name << endl;
    cout << "number : " << height << endl;
};
 
template <typename T>
void Person<T>::setName(string name){
    this->name = name;
}
 
template <typename T>
void Person<T>::setNumber(T height){
    this->height = height;
}
 
 
int main() {
//main 함수는 동일하다.
    Person<int> p1("Mr. Dev C++", 173);
    Person<string> p2("Ms. Unix", "155cm");
 
    p1.printAll();
    p2.printAll();
    cout << endl;
    p1.setNumber(188);
    p2.setNumber("2m 10cm");
    cout << endl;
    p1.printAll();
    p2.printAll();
    return 0;
```
