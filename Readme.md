# C structure

---

- 목차
    - C언어 특징
    - 함수 정리
    - 프로그래밍
    - 함수의 정의
    - 논리연산&비트연산
    - 메모리구조
    - 변수 유효 범위
    - 배열
    - 포인터
    - 스택프레임(stack frame)
    - 문자와 문자열
    - 구조체
    - 매크로 함수& 입출력
    - 조건부 컴파일
    - 비트연산

(참고: 내용이 많은 부분은 따로 페이지를 작성했습니다.)

## **C언어 특징**

- High level language 와 Low level language 특성을 모두 가지고 있고, 이를 절차 **지향 프로그래밍 언어**라 한다

- C언어의 장점
    - 다양한 하드웨어의 **이식성이 보장**된다 .(이식성이란 특정 환경에서 동작하는 SW를 다른  환경으로 변화해도 동작할 수 있는 능력)
    - **어썸블리어 수준으로 하드웨어를 제어가 가능**
- C언어의 단점
    - 시스템 자원을 제어할 수 있으므로 프로그램에서 조심을 기울여야한다.

## 함수 & 출력 변수 정리

자주 또는 가끔 사용하지만 알아 두어야 할 필수 함수와 출력 변수

[함수 정리](https://www.notion.so/60294f08f85b44318cdb6d6035556725?pvs=21)

## **프로그래밍**

- 프로그램을 실행하는 방식은 다음과 같다.
    1. **소스파일**: C , Py 등 대부분 high level에서 작성된 코드들
    2. **선행 전처리기**: #include, #define 등 #으로 시작하는 선행처리 지시자를 따라 실행됨.
    3. **컴파일**: 컴퓨터는 0,1 로 이루어진 기계어만 이해할 수 있으므로 소스 파일ex)C Python 을 0,1로 이루어진 기계어로 바꾸는 작업이 컴파일
    4. **오브젝트 파일** 컴파일 후 생성된 obj 파일의 경우 기계 언어에 해당함.o
    5. **시동코드**: obj 등 프로세스에서 작동시키기 위해서는 시동코드가 필요하다. 보통은 OS(Window, liunx)에서 지원을 하지만 OS가 없는 bare metal 환경에서는 시동코드까지 직접 개발자가 작성해야 한다.
    
    ![https://www.tcpschool.com/lectures/img_c_programming.png](https://www.tcpschool.com/lectures/img_c_programming.png)
    

참고: [https://www.tcpschool.com/c/c_intro_programming](https://www.tcpschool.com/c/c_intro_programming)

## 함수의 정의

![https://www.tcpschool.com/lectures/img_c_function_structure.png](https://www.tcpschool.com/lectures/img_c_function_structure.png)

## 논리연산&비트연산

- 논리연산자
    
    
    | 논리 연산자 | 의미 |
    | --- | --- |
    | && | AND |
    | || | OR |
    | ! | NOT |
- 비트연산자
    
    
    | 비트 연산자 | 설명 |
    | --- | --- |
    | & | AND |
    | | | OR |
    | ^ | XOR |
    | ~ | NOT |
    | << | left shift |
    | >> | right shift |

## **메모리 구조**

1. 코드(code) 영역
2. 데이터(data) 영역
3. 스택(stack) 영역
4. 힙(heap) 영역

![https://www.tcpschool.com/lectures/img_c_memory_structure.png](https://www.tcpschool.com/lectures/img_c_memory_structure.png)

## **변수의 유효 범위(variable scope)**

1. 지역변수(Local variable)
    - 블록 내에서 선언된 변수
    - 블록이 종료되면 메모리에서 삭제
    - Stack에 저장
2. 전역변수(Global variable)
    - 외부에서 선언된 변수
    - 프로그램 어디서나 접근할 수 있음. 프로그램이 종료 된어야만 메모리에서 사라짐
    - data영역에 저장되면 직접 초기화 하지 않아도 0으로 자동초기화
3. 정적변수 (Static variable)
    - static키워드로 선언한 변수를 의미
    - 지역, 전역 변수의 특징을 모두 가짐
    - 함수내에서 선언된 정적 변수는 전역변수와 같이 단 한번만 초기화되며 프로그램이 종료되어야 메모리상에서 사라짐
    - **즉 정적변수는 어디서 선언하던 전역변수와 같이 작용한다.**
    - 하지만 다른 프로그램 예를들어 main.c , test.c 양쪽에서 생성한 정적변수는 서로 사용할 수 없다. (단 전역 변수는 사용가능)
4. 레지스터변수(Register variable)
    - register키워드로 선언한 변수를 의미
    - 이렇게 선언한 register는 CPU 메모리에 저장되어 빠르게 접근할 수 있게 됩니다.

## 배열

[배열 및 주소값 출력](https://www.notion.so/c62fbcbedfc34d609a507e10e6a58651?pvs=21)

- 1차원 배열 vs 다차원 배열

![https://www.tcpschool.com/lectures/img_c_twodimensional_array.png](https://www.tcpschool.com/lectures/img_c_twodimensional_array.png)

## 포인터

- 포인터의 경우 내용이 많아서 따로 정리했습니다.
    
    [포인터](https://www.notion.so/d65edb5d436a4353aae63fb91f30626d?pvs=21)
    

## 메모리 동적할당

데이터 영역과 스택 영역에 할당되는 메모리의 크기는 컴파일 타임(compile time)에 미리 결정됩니다. 하지만 힙 영역의 크기는 프로그램이 실행되는 도중인 런 타임(run time)에 사용자가 직접 결정하게 됩니다. 

- 동적할당 사용 이유

한정된 메모리 공간에서 메모리를 효율적으로 사용하기 위해. 정적(전역,지역) 변수로 선언한 메모리는 프로세스가 끝날때 까지 계속해서 메모리 공간에 남아있는다. 하지만 동적 변수를 사용할 경우 사용할때만 메모리에 할당하고 사용을 안할 땐  free 를 사용하여 해제가 가능하다.

즉  stack은 컴파일 전 heap 영역은 컴파일 시간에 따라 크기가 결정

이렇게 런 타임에 메모리를 할당받는 것을 **메모리의 동적 할당(dynamic allocation)**이라고 합니다.

| 함수 | 기능 | 예시 |
| --- | --- | --- |
| malloc | 프로그램 런 중 heap 영역 메모리를 할당 | arr = malloc(arr_len*sizeof(int)) |
| free | 프로그램 런 중 heap 영역 할당된 메모리를 반환 | free(arr) |
| calloc | malloc과 동일 역할, 단 메모리 크기를 두 인수로 전달 받음. | calloc(arr_len, sizeof(int)) |
| realloc | 기존 메모리 위치에 충분한 공간시 추가 메모리 할당. 단 공간이 없다면 기존데이터를 복사 후 이어서 메모리공간 할당 |  |
- 예시 코드

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    int i, arr_len = 3; // 동적할당 길이
    int* ptr_arr; 
    int* ptr_arr2; 

    ptr_arr = (int*)malloc(arr_len * sizeof(int)); // 동적할당 길이 * 자료형
    ptr_arr2 = (int*)calloc(arr_len,sizeof(int));  // 동적할당 길이 * 자료형
    if(ptr_arr == NULL){
        printf("메모리 할당 실패");
        exit(1);   // error로 인한 실패 후 프로그램 강제종료시 1 ,
                   //정상적인 종료시 0, 이경우 return 0와 거의 같다.
    } 

    printf("malloc 동적할당으로 인한 메모리 초기 값\n");
    for(i = 0 ; i < arr_len ; i++){
        printf("%d ", ptr_arr[i]);
    }

    printf("\ncalloc 동적할당으로 인한 메모리 초기 값\n");
    for(i = 0 ; i < arr_len ; i++){
        printf("%d ", ptr_arr2[i]);
    }

    free(ptr_arr);
    free(ptr_arr2);
    return 0 ;
}
```

동적 할당을 하여 ptr_arr가 마치 배열처럼 사용된다.(배열 맞다.)

malloc 또는 colloc 앞에 (int*) 과 같이 포인터 자료형 선언 신경쓰자

## 문자와 문자열

[문자 문자열](https://www.notion.so/1ca56fd3731846f7a4e29e9e8c942f0b?pvs=21)

## 구조체

[구조체](https://www.notion.so/682217ba65f64c478a19e8d885bbe25c?pvs=21)

### 메크로 함수 & 입출력

출처: [https://www.tcpschool.com/c/c_prepro_macroFunc](https://www.tcpschool.com/c/c_prepro_macroFunc)

한번 읽어만 보자.

- 미리지정된 매크로 Predefined macro

Pre macro같은 경우 C언어에서 제공하고 있기 때문에 사용자가 재정의는 불가능

| Pre macro | 설명 |
| --- | --- |
| __DATE__ | 선행처리가 수행된 날짜를 "Mmm dd yyyy"형식으로 나타낸 문자열 |
| —TIME— | 선행처리가 수행된 시간을 "hh:mm:ss"형식으로 나타낸 문자열 |
| —FILE— | 현재 소스 파일의 이름을 나타내는 문자열 |

```c
int main(void){
    printf("선행처리가 수행된 날짜는 %s입니다.\n", __DATE__);
    printf("선행처리가 수행된 시간은 %s입니다.\n", __TIME__);
    printf("현재 소스 파일에서 처리중인 라인 번호는 %d입니다.\n", __LINE__);
    printf("__STDC__ : %d\n", __STDC__);
    printf("__STDC_HOSTED__ : %d\n", __STDC_HOSTED__);
    printf("__FUNCTION__ : %s\n", __FUNCTION__);
	
    return 0;}
```

```c
선행처리가 수행된 날짜는 Jan 24 2024입니다.
선행처리가 수행된 시간은 05:51:07입니다.
현재 소스 파일에서 처리중인 라인 번호는 6입니다.
__STDC__ : 1
__STDC_HOSTED__ : 1
__FUNCTION__ : main  //가장 많이 사용하는 함수. 어떤 함수에서 쓰였는지 확인
```

- 참고: #define의 경우 자료형을 선언하지 않는데 알아서 가장 적당한 자료형을 선언해주는 것으로 확인 (단 실수면 크기와 상관없이 double 부터 시작하는 것으로 예상)

ex) #define PI 3.14 하면 8byte의 double. 3 을 넣으면 4byte의 int 형 선언.

### 조건부 컴파일

if 문과 매우 유사하다. preprocess(#)을 앞에 붙여서 진행되는 방식

단 여기서 모든 조건은 define과 연관 있다. 정의된 함수의 조건 여부를 묻는 것이기에 전역변수나 지역변수로 선언된 변수와는 상관없다

| 지시자  | 용도 |
| --- | --- |
| if | 조건식 |
| ifdef | define 되었는지 |
| ifdef | define not 인지 |
| enif | 조건부 컴파일 종료 |

```c
#define COND 2

int main(void){	
	//int COND = 1; //만약 위 define을 주석 처리 후 실행해도 어떠한 조건문에도 해당되지 않음
// 정의 뿐만 아니라 값까지 확인
	#if COND == 1
		puts("매크로 상수 COND가 선언되어 있으며, 그 값은 1입니다.");
	#elif COND == 2
		puts("매크로 상수 COND가 선언되어 있으며, 그 값은 2입니다.");
	#endif
// 정의 여부만 확인
	#ifdef COND
		printf("COND 선언됨\n");
	#else // else 대신 ifndef를 사용해도 동일
		puts("COND 선언 안됨\n");
	#endif 
	return 0;
}
```

```c
매크로 상수 COND가 선언되어 있으며, 그 값은 2입니다.
COND 선언됨
```

### 비트연산

비트 연산자: OR, AND , XOR 등등…

비트 시프트: >> , <<

>> : 오른쪽으로 1비트씩 이동 빈공간은 1로 채움

<<: 왼쪽으로 1비트씩 이동 빈공간은 0으로 채움

비트 시프트 연산을 할경우 MSB에 저장되어있는 sign(부호)의 경우 건들지 않는다.(대부분의 시스템에서, 예외도 있다.)

### 음수 표현법

**1의 보수: 양수 값에서 NOT을 진행**

```c
양수: 0001: 1
음수: 1110:-1
```

- 장점: not 연산만으로 가능하다.
- 단점: -0 , +0 이동시에 존재

**2의 보수:  1의 보수에서 1을 더한다.**

(1의 보수 후 1을 더한다.)

```c
양수: 0001: 1
음수: 1111:-1
```

1의 보수의 단점인 0이 두개 존재하는 것이 사라진다.

소수의 방식:

- 고정 소수점:

![https://www.tcpschool.com/lectures/img_c_fixed_point.png](https://www.tcpschool.com/lectures/img_c_fixed_point.png)

- 부동 소수점

![https://www.tcpschool.com/lectures/img_c_floating_point_32.png](https://www.tcpschool.com/lectures/img_c_floating_point_32.png)

자료 출처:[https://www.tcpschool.com/c](https://www.tcpschool.com/c/c_function_variableScope)
