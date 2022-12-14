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
> 전역변수의 경우 다른곳에서 접근이 가능하여 값이 수정될 수 있어 STATIC을 걸어준다.


```
#include <stdio.h>

//전역변수 

int S(int a){
	static int count=0; //프로그램이 끝날때까지 소멸되지 않는다. 
	a *=a;
	count++;
	printf("%d번 실행\n", count);
	return a;
}


void main(void){

	int x; 
	while(1){
		scanf("%d",&x);
		if(x !=0){
			printf("%d\n", S(x));
			printf("%d\n",x); //파라미터로 넘겨주는 것은 데이터를 복사하는 것.! 
							  //그래서 함수의 연산에 영향을 받지 않음.	
		}else{
			break;
		}
	}
	return 0;
}
```

#### 배열과 포인터**
**😙포인터를 꼭 이해하자!**


##### 배열
배열은 동일한 자료 유형이 여러개 필요한 경우에 이용할 수 있는 자료구조
```
#include <stdio.h>

void main(void){
	
	int arr[5]; //arr은 원소를 5개 가짐. 
	arr[0]=1;
	arr[1]=2;
	arr[2]=3;
	arr[3]=4;
	arr[4]=5;

	printf("%d\n", arr[3]);
	
	return 0;
}
```

##### 이차원배열
```
#include <stdio.h>

void main(void){
	
	int arr[9][9];
	
	int i;
	int j;
	
	for(j=0; j<9; j++){
	  for(i=0; i<9; i++){
		 arr[j][i] = (j+1)*(i+1);
		}
	}

	for(j=0; j<9; j++){
	  for(i=0; i<9; i++){
		 printf("%d * %d = %d\n",j+1,i+1,arr[j][i]);
		}
	    printf("\n");
	}
	
	
	
	return 0;
}
```

#### 포인터
포인터 변수는 일반 변수와는 다르게 변수에 저장되는 값이 메모리의 주소값만 저장할 수 있는 특별한 변수.
변수 앞에 &를 붙이면 주소를 의미함. (scanf 사용할 때 &를 사용한 이유가, 그 값을 가르키는 주소로 액세스 하기 위함이다)

``` int a =3;
int *ptr =&a;
```


-> 포인트는 메모리 주소값만 저장할 수 있는 특별한 변수임. (포인터 변수도 메모리 주소를 갖고 있다.. 추가적으로 int를 사용한 이유는 a값의 자료형을 따라간다..)



```
#include <stdio.h>

void main(void){
	
	int a= 3;
	int *ptr = &a;	

}
```






```
#include <stdio.h>

void main(void){
	
	int a= 3;
	int *ptr = &a;	
	
	printf("ptr = %d\n", ptr);
	printf("&a = %d\n", &a);

}
```




참고로 ptr은 또 자기주소를 갖고 있다.


```
#include <stdio.h>

void main(void){
	
	int a= 3;
	int *ptr = &a;	
	
	printf("ptr = %d\n", ptr);  //a의 주소를 가지고옴 
	printf("&a = %d\n", &a);    //a의 주소를 가지고 옴. (위와 동일) 
	printf("&ptr = %d\n", &ptr); //ptr변수의 주소를 가지고옴 
	printf("*ptr = %d\n", *ptr); //주소에 있는 값을 가지고 옴 3 


}
```

### 포인터
- 메모리 주소를 가질수 있는 형이다.
- 메모리 주소값과 메모리 주소가 가르키는 위치에 있는 값을 다룰 수 있다.



```
#include <stdio.h>

void main(void){
	
	int a= 3;
	int *ptr = &a;	
	
	printf("ptr = %d\n", ptr);  //a의 주소를 가지고옴 
	printf("&a = %d\n", &a);    //a의 주소를 가지고 옴. (위와 동일) 
	printf("&ptr = %d\n", &ptr); //ptr변수의 주소를 가지고옴 
	printf("*ptr = %d\n", *ptr); //주소에 있는 값을 가지고 옴 3 

	(*ptr)++;  //포인트 주소로 접근하여 증가시켰음 (액세스가 가능하다) 
	printf("*ptr = %d\n", *ptr); // a가 4가됨! 
	printf("a = %d\n",a);	 

}
```



- \*(변수) : 변수값이 가르키는 값 ->간접값연산자
- \&(변수) : 변수의 주소  //scanf를 사용할때 예시를 기억하자. -> 주소연산자

 ####   배열과 포인터

🐡** 매우중요!!!****

arr == &arr[0]
*arr == arr[0]
*(arr+1) == arr[1]


### 다차원 배열과 포인터
 - arr == &arr[0][0]
 - *arr == arr[0][0]
 - *(arr+1) == arr[1][0]
 - *(arr+2) == ]arr[2][0]

 - *(*(arr+1)+1) == arr[1][1]
 - *(*(arr+1)+2) == arr[1][2]


```
#include <stdio.h>

void main(void){
	
	int arr[5];
	int i;
	for(i=0 ; i<5; i++){
		arr[i]=i;
	}
	for(i=0; i<5; i++){
		printf("arr[%d] =%d\n", i, arr[i]);
	}

	//1. 주소확인
	printf("\n\n%d\n",arr); //배열이름만 나오면 배열 주소가 조회된다. 
 	printf("%d\n", &arr[0]); //arr주소는 arr[0]의 주소
	printf("%d\n", &arr[1]); //arr주소는 arr[1]의 주소, 물리적으로도 연속적으로 증가함 4byte 만큼 증가하였음.!
	printf("%d\t %d", *(arr+1),arr[1]); 
	 	
}
```


```
#include <stdio.h>

void main(void){

	int arr[3][3];   
	int i,j;
	
	for(i=0; i<3; i++){
		for(j=0; j<3; j++){
		arr[i][j] = i;
		}
	}
	
	for(i=0; i<3; i++){
		printf("(arr+%d) = %d\n",i,arr+i);
		printf("*(arr+%d) = %d\n", i, *(arr+i));
		printf("arr[%d][0] = %d\n\n",i, arr[i][0]);
		
	}
	
	for(i=0; i<3; i++){
		for(j=0; j<3; j++){
			printf("(arr+%d)+%d = %d\n",i,j, *(*(arr+i)+j));
			printf("(arr+%d)+%d = %d\n",i,j, &(*(*(arr+i)+j)));
		}
	}
	


	 	
}
```

#### 문자열

```
#include <stdio.h>

void main(void){

	char str[6] ="Apple";
	printf("%s",str);
	 	
}
```
그런데, str은 문자열의 배열 주소가 나타나야 하는데 Apple이 나타난다. 그런데 printf(%s)로 출력하면 null이 나타날때까지 출력해준다.

### 스트림과 데이터의 이동
스트림을 '빨대'라고 생각하자. 
외부로 자료를 주고 받을 빨대가 필요하다!

### 문자 단위의 입출력 함수

```
#include <stdio.h>
int putchar(int c);
int fputc(int c, File* stream);
```

```
#include <stdio.h>
void main(void){
	int ch;
	ch= fgetc(stdin); //문자 입력 표준 스트림 
	fputc(ch, stdout); //문자 출력 
	return 0;
}
```

### 문자열 단위의 입출력 함수

```
#include <stdio.h>

void main(void){
	
	char *str1= "string";
	puts(str1);
	
	char str2[] ="apple";
	puts(str2);
	
	char str3[] = {'b','o','o','k'};
	puts(str3);
	
	return 0;
	
}
```

전송할때 논리적으로는 스트림, 물리적으로는 버퍼메모리를 통해 전송한다. 코드를 통하여 확인할 수 있다.

```
#include <stdio.h>

void main(void){
	
	
	
	char *str1= "string";
	fputs(str1,stdout);
	
	char str2[] ="apple";
	puts(str2);
	
	char str3[] = {'b','o','o','k'};
	puts(str3);
	
	return 0;
	
}
```
### 구조체, 공용체, 열거형
구조체의 경우 선언을 하고 자료형이 몇개가 있으면, 선언을 하면 메모리 공간에 확보를 한다. 결국 num1, num2, num3이 다른 값으로 출력된다. 
공용체의 경우에는 한 메모리공간에서 같이 사용된다, 변수 선언되면 기존 자리에 계속 덮어쓴다. 그래서 결국 num1, num2,num3을 출력할때 num3이 출력된다.





### 함수와 포인터
- 함수를 호출하면서 매개변수로 배열을 넘겨주는 방법이 없다.
- 함수 내에서 배열에 접근할 수 잇도록 할려면 배열의 주소값을 전달해야 한다.

```
#include <stdio.h>

int arrSum(int *x, int len){ //포인트 변수로 받아줌
	int i, sum=0;
	for(i=0; i<len; i++){
	 	sum+=*(x+i);
	 	 	
	}
	
	return sum;
}

void main(void){
	int arr[5] = {1,2,3,4,5};
	int res;
	res = arrSum(arr, sizeof(arr)/sizeof(int)); //arr[0]의 주소임. size구하는 방법 특이함.. :)
	printf("%d\n", res);
	
}
```

위에서는 포인터로 넘겨주기 때문에 함수에서 arr에 직접 변경이 가능함. (이전에 함수는 파라미터는 값을 바꿀수 없었음)
```
#include <stdio.h>

void arrTest(int *x, int len){
	int i, sum=0;
	for(i=0; i<len; i++){
	 	*(x+i) *= 2;	 	
	}
	
}



void main(void){
	int arr[5] = {1,2,3,4,5};
	int i;
	arrTest(arr, sizeof(arr)/sizeof(int));
	
	for(i=0; i<sizeof(arr)/sizeof(int); i++){
		printf("%d\t",arr[i]);
	}
}
```

### Call by Value vs Call by Reference
- value: 값으로 전달
- reference: 주소로 전달
1.
```
void incrementByValue(int number){ 
number ++;
}
```

2.
```
void incrementByReference(int* number){
(*number)++;
}
```

2번의 경우 경우 포인터 값으로 받아서 number의 값이 증가한다.

```
#include <stdio.h>

void incrementByValue(int number){
	number++;
}

void incrementByReference(int* number){
	(*number)++;
}

void main(void){
	int number=2;
	
	incrementByValue(number);
	printf("number: %d\n",number);
	
	incrementByReference(&number);
	printf("number: %d\n",number);
	
	
}
```

swap 알고리즘

```
#include <stdio.h>

void Swap(int* a, int* b){
	int temp;
	temp = *a;
	*a= *b;
	*b= temp;
	
}

int main(void){
	int num1 =5;
	int num2= 10;
	printf("num1 : %d\tnum2: %d\n",num1, num2);
	
	Swap(&num1, &num2);
	printf("num1: %d\tnum2 :%d\n",num1, num2);
	return 0;
	
	
}
```
**C는 swap할때 포인터 변수 사용해야함. 일반변수는 값이 소멸해서 바뀌지 않음(다른 언어와 차이).**

#### 😎 내가 짠 swap을 이용한 버블정렬 ####

```
#include <stdio.h>

void Swap(int *a, int *b){
	int temp;
	temp = *a;
	*a= *b;
	*b= temp;
}



void Sort(int *arr, int arrlen){
	int i, j;
	for(i=0; i<arrlen-1; i++){
		for(j=0; j<arrlen-1-i; j++){
			if(*(arr+j)>*(arr+j+1)){
				Swap(arr+j, arr+1+j);
			}
		}
	}
}


int main(void){
	int arr[5];
	int i, arrlen;
	
	arrlen = sizeof(arr)/sizeof(int);
	for(i=0; i<arrlen; i++){
	
		printf("arr[%d]:",i);
		scanf("%d",&arr[i]);
	}

	Sort(arr, arrlen);

	for(i=0; i<arrlen; i++)
		printf("arr[%d]:%d\n",i,arr[i]);
			
	
	return 0;
}
```


### 포인터 대상의 Const 선언

앞에서 배울때 Const는 상수로 배웠다.
<예시>

```
#include <stdio.h>

int main(void){
	int num =20;
	const int *ptr = &num;
	*ptr =30;
	num =40;
}
```
 위의 코드는 컴파일 에러가 발생한다. \*ptr=30 에서 에러가 존재한다.
 
 ```
 #include <stdio.h>

int main(void){
	int num1 =20;
	int num2 =30;
	int* const  ptr = &num1;
	ptr = &num2;
	*ptr =40;
}
```
위의 경우에도 [Error] assignment of read-only variable 'ptr' 가 발생한다.

```
#include <stdio.h>

void ShowArr(int *arr, int len){
	int i;
	for(i=0; i<len; i++){
	printf("%d ",*(arr+i));
	}
	printf("\n");
	
}



void main(void){
	
 int arr1[3] = {1,2,3};
 int arr2[5] = {4,5,6,7,8};
 
 int lenarr1 = sizeof(arr1)/sizeof(int);
 ShowArr(arr1, lenarr1);
 
  int lenarr2 = sizeof(arr2)/sizeof(int);
  ShowArr(arr2, lenarr2);	
 
 
 return 0; 

}
```
 
