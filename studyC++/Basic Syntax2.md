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
