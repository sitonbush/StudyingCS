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
