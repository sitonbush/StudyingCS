### 간단한 함수 만들기

```
#include <stdio.h>

int Add(int num1, int num2){
	return num1+num2;
}

void main(void){
	int x, y, res;
	x= 5; y=2;
	
	res= Add(x,y);
	printf("%d\n",res);
	
}
```
다른방식

```
#include <stdio.h>

int Add(int num1, int num2);
void main(void){
	int x, y, res;
	x= 5; y=2;
	
	res= Add(x,y);
	printf("%d\n",res);
	
}


int Add(int num1, int num2){
	return num1+num2;
}
```

Return의 의미
-함수를 빠져나간다.
-값을 반환한다.


### scanf, switch, 함수를 이용한다.

```
#include <stdio.h>
double triangle(int x, int y){
	double result= (double)x*y/2;
	return result;
}

int rectangle(int x, int y){
	return x*y;
}

double circle(int x){
	return (double)(x*x*3.14);
}


void main(void){
	//도형을 고릅니다. 
	printf("1. 삼각형\n2.사각형\n3.원\n");
	printf("도형을 고르세요\n");
	int shape;
	scanf("%d",&shape);
	//x y값을 입력하세요
	int x, y;
	printf("x,y값을 입력하세요\n");
	scanf("%d %d",&x,&y);
	
	switch(shape){
		case 1:
			printf("%.2f 입니다",triangle(x,y));
		break;
		
		case 2:
			printf("%d 입니다",rectangle(x,y));
		break;
		
		case 3:
			printf("%.2f입니다",circle(x));
		break;
		default:
			printf("잘못 입력하였어요\n");
		
	} 

}
```


#### 변수의 수명과 범위- 지역변수
 - 중괄호 내에서 선언된 변수는 모두 지역변수이다. 
 - 지역변수는 선언된 지역 내에서만 유효하기 때문에 선언된 지역이 다르면 이름이 같아도 문제가 되지 않는다. 
 - 지역변수는 반복문이나 조건문에도 선언이 가능하다.
 - 함수를 정의할 떄에 선언하는 매개변수도 지역변수 이다.

#### 변수의 수명과 범위- 전역변수
 - 프로그램이 처음 실행되면 메모리 공간에 할당되어 프로그램이 종료될때까지 메모리 공간에 남아있는 변수이다.

```
#include <stdio.h>

//전역변수 
int count =0;

void test1(void){
	count++;
}

void main(void){

	test1();
	test1();
	test1();
	printf("%d",count);
		
	return 0; 

}
```

> result :3

```
#include <stdio.h>

//전역변수 
int count =0;

void test1(void){
	count++;
}

void test2(void){
	int count=0;
	count++;
}


void main(void){

	test2();
	test2();
	test2();
	printf("%d",count);
		
	return 0; 

}

```

> result=0;

지역변수는 함수가 끝나면 소멸되기 때문에 결과값은 0이다.


#### 기억클래스(Storage Class)
 - 자동변수  :default
 - 정적변수😙  : 전역변수와 비슷하나 차이점이 존재함. 원시 프로그램의 내부 어디서나 사용이 가능하다. 
 - 외부변수 : 모든 원시프로그램에 걸쳐 사용되는 변수이다.
 - 레지스터변수 : 지역변수에서만 사용이 가능하고, 고속 연산용 변수이다.


😲**전역변수**
STATIC 실행하면, 메모리에 저장됨. 

```
#include <stdio.h>

//전역변수 

void multiply (int x){
	static int count=0;	
	count++;
	printf("거듭제곱은 : %d\n",x*x);
	printf("count : %d",count);

}



void main(void){

	while(1){
		int x;
		scanf("%d",&x);
		if(x==0){
			break;
		}
		multiply(x);
	}

		
	return 0; 

}
```

> COUNT가 누적됨을 확인할 수 있다. STATIC이 붙어 있지 않으면 COUNT는 계속 0이다.
> STATIC변수는 선언한 함수에서만 접근이 가능하고(접근이 외부에서 안된다-전역변수와 차이점), 대신 함수가 종료되도 메모리에 유지됨.

