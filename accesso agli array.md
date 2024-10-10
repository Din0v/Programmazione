# Acedere gli array
si accede in lettura e scrittura agli [[Array]] in questo modo:

```c 
#include <stdio.h>

int main(){
	int a[5]={0,1,2,3,4}; //parentesi graffa

	printf("%d", a[0]); // accesso di lettura del primo elemento 
	printf("%d", a[3]); //accesso di scrittura del quarto elemento

	a[0]= 12; //accesso di scrittura.
	a[3]= 69; //accesso di scrittura.
	
}
```

- gli elementi degli array iniziallizata vengono scritti tra parentesi graffe. 
- parentesi **Quadre** per leggere o scrivere un elemento nel array.
- 
