

storage class specifier
  * typedef
  * extern
  * static
  * auto

### typedef ###

typedef는 저장소 클래스 지정자(storage class specifier)중 하나입니다. 

사용법은 

>typedef 재정의할_자료형 재정의된_이름
> 
>typedef unsigned int MYUINT;
> ~~MYUINT num~~

이는 복잡한 타입을 간단히 만들 수 있다. 예를들어

```c++
std::vector<std::pair<std::string,int>> pairlist; 

bool hasDuplicates(std::vector<std::pair<std::string, int> > pairlist){
    // some code here 
}
```
를 다음과 같이 바꾸면 좀 더 간단히 만들 수 있다.

```c++
typedef std::vector<std::pair<std::string, int>> pairlist_t;  // make pairlist_t an alias for this crazy type 

pairlist_t pairlist; // instantiate a pairlist_t 

bool hasDuplicates(pairlist_t pairlist){ // use pairlist_t in a function parameter 
    // some code here 
}
```

### 디폴트 인수 ###

함수 쓸떄 디폴트 인수로 써준다.

### 인수 전달 방법 ###
1. call by value
2. **call by reference**
3. call by pointer

그중 2. call by reference로 변수의 값을 복사하는것이 아닌, 원본 데이터를 직접 전달하는것입니다. 이는 3. call by pointer로도 가능하지만, 참조자(reference)를 사용하여 전달하는 방법입니다. 

#### 참조자 ####
c++에서는 참조자 &를 지원하는데 이때 &는 주소연산자에서의 &와 다릅니다.

>int 변수_이름
>int& 참조자이름=변수이름

으로 선언하고, 1. 참조자는 선언과 동시에 초기화 해야하며, 2. 참조하는 대상과 타입이 당연히 일치해야 하며 3. 한번 초기화되면 **참조하는 대상**을 변경할 수 없습니다.

int& 는 int형 변수에 대한 참조르 의미하며, 이렇게 선언된 참조자는 대상 변수와 같은 메모리 위치를 참조하게 됩니다.
```c++
nt x = 10; // 변수의 선언
int& y = x; // 참조자 선언

cout << "x : " << x << ", y : " << y << endl;
y++;        // 참조자를 이용한 증가 연산
cout << "x : " << x << ", y : " << y << endl;
cout << "x의 주소값 : " << &x << ", y의 주소값 : " << &y;
```
의 결과로

>x : 10, y : 10
>
>x : 11, y : 11
>
>x의 주소값 : 0x7ffe6c0a1234, y의 주소값 : 0x7ffe6c0a1234

가 나옵니다.

* 주로 참조자는 함수의 인수로서 전달합니다. 

함수가 참조자로 인수를 받으면, 참조자가 참조하는 실제 변수값을 함수 내에서 조작 할 수 있습니다.

```c++
int main(void)
{
    int num1 = 3, num2 = 7;
    cout << "변경 전 num1의 값은 " << num1 << "이며, num2의 값은 " << num2 << "입니다." << endl;
    Swap(num1, num2);
    cout << "변경 후 num1의 값은 " << num1 << "이며, num2의 값은 " << num2 << "입니다." << endl;
    return 0;
}
 
void Swap(int& x, int& y)
{
    int temp;
 
    temp = x;
    x = y;
    y = temp;
}
```
의 결과로

>변경 전 num1의 값은 3이며, num2의 값은 7입니다.
>
>변경 후 num1의 값은 7이며, num2의 값은 3입니다.

가 나옵니다.

* 이러한 함수의 매개변수로 전달하는 참조자는, 매개변수를 복사하지 않아도 되기 때문에, c++에서 사이즈가 큰 구조체를 인수로 전달할때 유용합니다.
``` c++
struct Book
{
    string title;
    string author;
    int price;
};
 
void Display(const Book&);
 
int main(void)
{
    Book web_book = {"HTML과 CSS", "홍길동", 28000};
    Display(web_book);
    return 0;
}
 
void Display(const Book& bk)
{
    cout << "책의 제목은 " << bk.title << "이고, ";
    cout << "저자는 " << bk.author << "이며, ";
    cout << "가격은 " << bk.price << "원입니다.";
}
```
의 결과로

>책의 제목은 HTML과 CSS이고, 저자는 홍길동이며, 가격은 28000원입니다.

가 나옵니다.

* 마지막으로 reference의 다른 장점으로 class의 중첩이 있을경우 쉽게 접근 할 수 있습니다.
```c++
#include <iostream>
using namespace std;

class Something { 
public:
	int value1; 
	float value2; 
}; 

class Other { 
public:
	Something something; 
	int otherValue; 
}; 

int main(){
	Other other1;

	int& ref= other1.something.value1=10;
	cout<<other1.something.value1<<endl;
	cout<<ref<<endl;
}
//출력 결과 
10
10
```

### inline ###

### namespace ###
 
1. namespace 정의 및 헤더에 선언
2. namespace global, local
3. 특정 namespac만

### 함수 포인터 ###







