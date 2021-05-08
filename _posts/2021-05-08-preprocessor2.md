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

이는 주로 조건부 컴파일을 할때 사용됩니다.
