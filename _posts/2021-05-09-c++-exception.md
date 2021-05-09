
### try , throw, catch ###

예외(exception)란 컴퓨터 시스템이 동작하는 도중에 예상하지 못한 오류가 발생하여, 실행되던 프로그램이 중지되는것을 의미합니다.

예외처리는 이러한 예외 상황을 처리 할 수 있도록 코드의 이름을 바꾸는 행위를 의미합니다. c++에서는 예외처리 문법으로 try, throw, catch를 제공합니다.

1. try 문: 예외 발생 가능성이 있는 코드블록
  
  * try{} 괄호 안에 예외 처리 대상 코드를 작성합니다.
  
2. throw 문: try문에서 발생한 예외상황일때 이 명령어를 예외적으로 던집니다. 이때 던진 변수는 catch에서의 매개변수로 들어갑니다.

3. catch 절: 발생한 예외에 대하여 예외처리 할 내용을 담을 코드블록을 의미합니다.

>try{
>    if(예외조건)
>       throw 예외객체;
>} catch ( 타입 예외객체 ){
>      예외처리;
>}

굳이 이렇게 안해도 되고, 실행시 try, throw, catch순으로 나오게하면 된다(?)

note)

* catch문은 예외가 발생될때만 실행되므로, 읽을땐 없다고 봐도 무방합니다.
* catch문은 오직 throw로만 이동가능합니다, goto로도 가능하지 않습니다.
* catch문은 여러개 만들 수 있습니다.(오버로딩 가능)

오버로딩은 매개변수의 종류, 갯수, const 유무에 따라 호출되는 함수가 다르지만,

catch문은 switch문처럼 제일 첫번째 예외부터 순차적으로 비교가 이루어지고 결정됩니다.

```c++
#include <iostream>
using namespace std;
 
int IncreaseNumber(int n){
    if (n < 0)
        throw n;
    else if (n == 0)
        throw "0은 입력할 수 없습니다.";
    return ++n;
}
 
int main(void){
    int num;
 
    cout << "양의 정수를 하나 입력해주세요 : ";
    while (cin >> num){
        try{
            cout << "입력한 정수에서 1을 증가시킨 값 : " << IncreaseNumber(num) << endl;
        }
        catch (int input){
            cout << input << "은 양의 정수가 아닙니다." << endl;
            cout << "양의 정수를 다시 입력해주세요 : ";
            continue;
        }
        catch(const char* st){
            cout << st << endl;
            cout << "양의 정수를 다시 입력해주세요 : ";
            continue;
        }
        break;
    }
    return 0;
}
```

C++에서 예외 처리는 다음과 같은 순서로 진행됩니다.

1. try 문에 도달한 프로그램의 제어는 try 문 내의 코드를 실행합니다.

2. 이때 예외가 발생(throw)하지 않으면 프로그램의 제어는 맨 마지막 catch 절 바로 다음으로 이동합니다.

3. 만약 예외가 발생하면 catch 핸들러는 다음과 같은 순서로 적절한 catch 절을 찾게 됩니다.

   3-1. 스택에서 try 문과 가장 가까운 catch 절부터 차례대로 검사합니다.

   3-2. 만약 적절한 catch 절을 찾지 못하면, 바로 다음 바깥쪽 try 문 다음에 위치한 catch 절을 차례대로 검사합니다.

   3-3. 이러한 과정을 가장 바깥쪽 try 문까지 계속 검사하게 됩니다.

   3-4. 그래도 적절한 catch 절을 찾지 못하면, 미리 정의된 terminate() 함수가 호출됩니다.

4. 만약 적절한 catch 절을 찾게 되면, throw 문의 피연산자는 예외 객체의 형식 매개변수로 전달됩니다.

5. 모든 예외 처리가 끝나면 프로그램의 제어는 맨 마지막 catch 절 바로 다음으로 이동합니다.

