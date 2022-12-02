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

```
#include <stdio.h>
void main(void){

int a=3;
printf("%d\n",a++);
printf("%d\n",a);

}

```

>출력 결과 3,4
++이 앞에 뒤에 붙는지 차이: 실행시키고 나서 연산이 수행되는지 여부.


나머지 연산자

```
#include <stdio.h>
void main(void){

int a=3;

printf("%d\n",6%3);
}
```

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

