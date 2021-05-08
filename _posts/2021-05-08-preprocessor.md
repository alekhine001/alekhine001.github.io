

전처리중, #define 매크로, #if, #ifdef 등이 있습니다. 그중 이글에선 #define 매크로만 다룹니다.

# #define 매크로 #

   #define의 usage에는 단순매크로, 함수 매크로,내장 매크로 가 있습니다.
  
### 1. 단순매크로 ###
  
> define MAX 100
  
> define PI 3.14
   
> define TAX_RATE 1.6
 
처럼 단순히 자주사용하는 숫자를 치환하는 용돌도 사용됩니다.

이는 
  
1. 가독성이 높아집니다. 
    
  단순히 코드를 숫자 1.6으로 사용하면 무슨 의미인지 모르지만, TAX_RATE라 설정하면, 코드를 수정할때 한눈에 알기 쉽습니다.
      
2. 상수 변경이 매우 용이해집니다.
    
  만약 큰 프로그램에 자주 쓰이는 상수를 변경해야 한다면, DEFINE 매크로를 통해 값만 변경하면 모든 숫자를 변경할 번거러움을 덜 수 있습니다.

``` c++
#include <iostream>
#include "head.h"

#define COUT cout                         // 명령어 또한 단순 매크로로 바꿀 수 있습니다
#define TEN 10                            // 상수를 매크로 사용합니다

using namespace std;

int main(void) {
	int result= sum(3,4);
	COUT<<result<<' '<<TEN<<endl;
	return 0;
}
```
### 2. 함수매크로 ###
#define 을 통해 마치 함수인것처럼 흉내를 낼 수 있습니다.

사용 방법은 다음과 같습니다.

> define 매크로(arg1, arg2, arg3...) 치환_텍스트

`#define SQUARE(x) x*x`




