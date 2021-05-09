### 파일 입출력 ###

컴퓨터 파일에는 두종류 (바이너리 파일, 텍스트 파일)이 있습니다.

* 바이너리 파일은 데이터의 저장과 처리 목적으로 0과 1의 이진형식으로 코딩된 파일을 가르킵니다. 읽거나 쓸때 변환이 일어나지 않습니다.
* 텍스트 파일은 사람이 알아 볼 수 있는 문자열로 이루어진 파일입니다. 프로그램이 이 파일의 데이터를 읽거나 쓸때 포맷 형식에 따라 변환이 일어납니다.

C++에서는 파일의 입출력을 *표준입출력* 처럼 처리합니다. 

* *표준 입출력*은 iostream *헤더파일*의 *istream* *클래스*와 *ostream* *클래스*의 멤버함수로 처리합니다.
* *파일 입출력*은 fstream *헤더파일*의 클래스 라이브러리(파일의 입력: *ifstream* 클래스, 파일의 출력: *ofstream*클래스)로 처리합니다. 

특정 파일과의 연결은 open() *멤버함수* 를 사용하여 다음과 같이 수행합니다.
>ifstream ifs;            // ifs라는 ifstream *객체*를 생성함.
>
>ifs.open("example.txt"); // ifs를 example.txt와 연결함.

혹은 한줄로

>ifstream ifs("example.txt");

로  쓸 수 있다.

생성한 입출력 파일객체의 수명이 다하면

>ifs.close()

로 닫을 수 있다.

추가로, open()함수에는 ifstream, ofstream에 따라 디폴트 인수로 각각 ios_base::in, ios_base::out|ios_base::trunc를 제공하는데, 

이 ios_base::in (혹은 out, ate, app, trunc, binary)는 파일 모드 상수라고 합니다.
