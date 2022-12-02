# C언어의 특징

- 시스템 프로그래밍 언어로 적합하다.
- 컴파일러 기법을 사용한다.
- 이식성이 높다. (하드웨어에 이입하기가 좋다-> 자바는 JVM이 돌아가는 곳에서만 사용이 가능함)
- 절차지향적 특성을 지닌다. 객체지향과 상반되는 개념은 아닌, 절차지향이 더 확장된 개념이다. 구조화 언어라고 부를수 잇는 제어구조와 제어문을 가지고 있다. 코드가 순차적으로 실행된다. 
- 포인터의 사용이 가능하다.

 ```
#include <stdio.h>

void main(void)
{
	printf("Hello World!\n");
}
 ```


### 변수와 연산자, 데이터 표현방식
- 예약어: 시스템이 알고 있는 특수한 기능을 수행하도록 이미 용도가 정해져 있는 단어
- 식별자: 사용자가 직접 정의하여 사용하는 여러 단어를 말한다.
*식별자 작성 규칙
-영문 대소문자,숫자, 밑줄의 63개뿐
-식별자의 첫 글자는 숫자를 사용할 수 없다.


### 변수
- 수학: 정해져 있지 않은, 임의의 값을 대입할 수 있는 문자
- 프로그래밍에서 변수: 값을 저장할 수 있는 메모리 공간에 붙은 이름, 혹은 **메모리 공간 자체**
<변수선언>
이름(변수명) -> 속성들(자료형) -> 값(주소/참조)

### 연산자
- 특정연산을 요구할 대 사용한느 약속된 기호

```
#include <stdio.h>
void main(void){

int a=3;
a++;
printf("%d\n",a);

}


```
#include <stdio.h>
void main(void){

int a=3;
printf("%d\n",a++);
printf("%d\n",a);

}



>출력 결과 3,4
++이 앞에 뒤에 붙는지 차이: 실행시키고 나서 연산이 수행되는지 여부.


나머지 연산자

```
#include <stdio.h>
void main(void){

int a=3;

printf("%d\n",6%3);
}


-C언어는 boolean 자료형이 없다. 다만 0거짓, 그외는 참으로 표현된다.
```
#include <stdio.h>
void main(void){

int a=3;
printf("%d\n",6>3);
}
```
> 1을 반환한다.

- 논리연산자
  - && 둘다 참일때 1 반환
  - || 둘중 하나가 참일때 1 반환
  - !  둘다 거짓일때 1반환 

```
#include <stdio.h>
void main(void){

int a=3;
printf("%d\n",!1);
}
```
- 조건연산자  조건? 참:거짓  

```
#include <stdio.h>
void main(void){

printf("%d\n", 3>4? 1:0 );
}
```

- sizeof 연산자 : sizeof(형)

```
#include <stdio.h>
void main(void){

printf("%d\n", sizeof(int) );
}
```

- 1byte의 크기는 8bit 이다. 


### 데이터를 표현하는 방식

- bit
- byte 8bit는 1byte이다.

```
#include <stdio.h>
void main(void){

	int num1 = 10;        //10진수
	int num2 = 0xA;       //16진수 0x
	int num3 = 012;       //8진수  0
	int num4 = 0b1010;    //2진수  0b
	
	printf("%d,%d,%d,%d",num1, num2, num3, num4);
}
```
> 결과 : 10, 10, 10, 10

<br></br>
------------------------
### 자료형 
자료형은 데이터를 표현하는 기준, 즉 code를 정의한다.

### 상수
변경이 불가능한 데이터. 상수도 메모리가 필요하다. 변수와 달리 이름이 없는 상수를 가리켜 '리터럴 상수' 혹은 '리터럴'이라고 한다.

### CONST 상수
심볼릭 상수는 변수처럼 이름을 지니는 상수이다. Const 키워드를 사용하는 방법과 매크로를 이용하는 방법이 있다.
선언과 동시에 값을 대입해야 한다. 선언만 하면 컴파일 에러가 발생한다.

'''
#include <stdio.h>

void main(void){
	const int A= 2;
	A=3;   //compile error occurred.
	printf("%d\n",A);
}
'''

>상수의 이름은 모두 대문자로 표시하고 두이상의 단어를 연결할 때에는 언더바('\_')를 사용한다.

### 변수
C언어는 선언만 하면 쓰레기값이 들어가 있다. (자바의 경우 0이 들어가 있음)

### 다른 자료형의 계산
```
#include <stdio.h>

void main(void){
	int a= 3.94+5.12;
	printf("%d\n",a);
}
```
묵시적 형변환-> 소수점 아래는 버림

```
#include <stdio.h>

void main(void){
	float a= 3.94+5.12;
	printf("%d\n",a);
}
```

위와 같이 출력하면 알 수없는 값이 나오는데 이는 "%d"로 출력된다. 이는 코드가 달라서이다!
```
#include <stdio.h>

void main(void){
	float a= 3.94+5.12;
	printf("%f\n",a);
}
```

### Printf 함수
- printf 함수는 문자열을 출력하는 함수이다.
- GUI환경에서는 이벤트 환경에서 입출력이 다양하게 있다. printf는 console환경에서 사용


### SCANF 함수
-printf 함수의 상대적인 기능인 입력(키보드)의 기능을 지닌다.

```
#include <stdio.h>

void main(void){

	int a;
	scanf("%d",&a);
	printf("%d\n",a);

}
```
소문자-대문자 변환
```
#include <stdio.h>

void main(void){

	char a;
	scanf("%c" , &a);
	int gap= 'A'-'a';
	
	printf("%c\n",a+gap);

}
```
지금까진 자료형을 보았다. 
---------------------------------------------
제어

### 반복문, 조건문

###### 반복문
- while

```
#include <stdio.h>

void main(void){

	int num = 0;
	while(num < 3){
	 printf("Hello \n");
	 num++;
		
	}
}
```

```
#include <stdio.h>

void main(void){

	int num = 1;
	while(num <=10){
	 printf("%d\n", num);
	 num++;
		
	}
}
```
-Do While

```
#include <stdio.h>

void main(void){

	int num = 3;
	do{
	  num++;
	  printf("%d\n", num);
	}while(num > 10);
	
}


### 반복문-for 문

```
#include <stdio.h>

void main(void){

	int i = 0;
	for(i=0; i<=10; i++){
		printf("%d\n",i);
	}	
}
```

>아래와 같이 사용해도 동일하게 작동하지만 가독성은 떨어진다.

```
#include <stdio.h>

void main(void){

	int i =0;
	for(; i<=10;){
		printf("%d\n",i);
		i++;
	}
		
}


<무한루프>

```
#include <stdio.h>

void main(void){

	int i =0;
	for(;;){
		printf("%d\n",i);
		i++;
	}
		
}

>구구단

```
#include <stdio.h>

void main(void){

	int dan = 2;
	int i;
	for(i=1; i<10; i++){
		printf("%d * %d = %d\n", dan, i, dan*i);
	}
		
}

>중첩포문

```
#include <stdio.h>

void main(void){

	int dan, i;
	
	
	for(dan=2; dan<10; dan++){
		for(i=1; i<10; i++){
			 printf("%d * %d = %d\n", dan, i, dan*i);
		}
		printf("\n");
	}
		
}

> scanf 이용
```
#include <stdio.h>

void main(void){

	int dan, i;
	scanf("%d", &dan);
	
		
		for(i=1; i<10; i++){
		 	printf("%d * %d = %d\n", dan, i, dan*i);
		}
		
}


### 조건문- IF

```
#include <stdio.h>

void main(void){

	int val;
	printf("정수 입력: ");
	scanf("%d", &val);
	
	if(val>0){
		printf("양수를 입력하셨습니다.");
	}
	
}

>다른 예시 

```
#include <stdio.h>

void main(void){

	int val;
	printf("정수 입력: ");
	scanf("%d", &val);
	
	if(val>0){
		printf("양수를 입력하셨습니다.");
	}else if(val ==0){
		printf("0 입니다.");
	}else{
		printf("양수가 아닙니다.");
	}
	
}

>팩토리얼 만들기
```
#include <stdio.h>

void main(void){

	int factorial, result;
	result=1;
	
	printf("Input factorial: ");
	scanf("%d", &factorial);
	
	while(factorial>1){
		result*=factorial;
		factorial -= 1;
	}
	printf("factorial result is %d", result);		
	
	
}




