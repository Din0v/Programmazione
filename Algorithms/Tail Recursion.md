# Tail Recursion 
- Is a special case of [[Recursion]]
- they are carachterized as having nothing to do during the $unwinding$ phase!. 
- in many cases the compiler detects it automatically,

Esempio: 
```c
// this is a tail recursion function
#include <stdio.h>

int facttail (int n, int a){

if (n < 0)
	return 0;
else if (n == 0)
	return 1;
else if (n == 1)
	return a;
else
	return facttail(n-1, n*a);
}
  
int main(){
	printf("Factorial is %d", facttail(12,1));
		return 0;
}

```

![[Pasted image 20220926163054.png]]

![[Pasted image 20220926163137.png]]

### Tags 
#Algorithms 
#Recursion 