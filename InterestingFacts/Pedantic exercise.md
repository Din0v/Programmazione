# interesting problem
```c 
#include <stdio.h>
int x = 0;

int f1 (int w){
int z = w + x++;
	{int z = w + x++;}
return z;
}

int main(){

printf("%d %d\n", f1(10), f1(10)); // problema numero 1 qui in questo formato adiacente
```

Compila Così: 

![[Pasted image 20220616230526.png]]

primo trucco nel come vengono effetuate le chiamate alla funzione **f1**, 
seconda cosa sono le parentesi graffe nella linea ==8== 
Non ho capito il perchè 





### Tags 
#interesting_fact 
