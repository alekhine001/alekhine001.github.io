전처리중 #if 와 #endif,   ifdef과 #endif,   그리고 #ifnef와 #undef 에 대하여 작성했습니다.

### 1. #if와 #endif ###

if와 elif처럼 #if와 #else 또한 있으며, 주의할점은 마지막에 endif를 적어줘야 합니다.

>#if 조건1
>
>문장 1
>
>#elif 조건2
>
>문장 2
>
>#else
>문장 3
>
>#endif

```c++
#include <iostream>
using namespace std;

#define TEST 34

int main(){
	
#if TEST==10
	cout<<"TEST IS 10"<<endl;
#elif TEST==20
	cout<<"TEST IS 20"<<endl;
#else 
	cout<<"TEST IS NOT 10 OR 20"<<endl;
#endif
	return 0;
}
```

### 2. #ifdef와 #endif ###

#if와 비슷하지만, ifdef는 정의된 매크로가 존재하기만 하면 되는것입니다.

>ifdef 매크로
>
>문장 1
>
>else 
>
>문장 2
>
>endif

```c++
#include <iostream>
using namespace std;

#define TEST 

int main(){
	
#ifdef TEST
	cout<<"TEST IS DEFINED"<<endl;
#else 
	cout<<"TEST IS UNDEFINED"<<endl;
#endif
	return 0;
}
```

### 3. #ifdef와 #if 의 용도 ###

#ifdef와 #if 는 특정 상황에서는 컴파일 하고, 그렇지 않은 상황에서는 컴파일을 하지 않거나 (혹은 안해도 상관없는 경우) 종종 사용됩니다.

특히 디버깅을 할경우 종종 사용됩니다. #DEBUG 매크로를 설정해두어 디버깅할경우 1, 아닐경우 0으로 설정하여 실행합니다.

```c++
#include <iostream>
using namespace std;

#define DEBUG 0

int main(){
	int counter=10;

#if DEBUG ==1
	cout<<"Debugging"<<endl;
#else
	cout<<"Not Debugging"<<endl;
#endif

#ifdef DEBUG
	cout<<"counter= "<<counter<<endl;
#endif
	return 0;
}
```
### 4. #undef와 #ifndef ###

#undef는 #def된 매크로를 없앨때 사용합니다. 프로그램이 커지면 매크로 또한 많아지기때문에, 매크로를 이중으로 정의하는 실수가 생기기 대문에 다 사용한 매크로는 #undef로 취소시킵니다.

#ifndef는 주로
``` c++
#ifndef MACRO
#define MACRO

//헤더파일의 내용
#endif
```
로 종종 사용되며, 헤더파일의 이중포함을 방지합니다. 먼저 MACRO가 정의되어 있는지 살펴본 후, 만약 정의되어 있지 않다면(if not defined, ifndef)바로 다음 아래줄에서 이를 정의합니다.


