

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

