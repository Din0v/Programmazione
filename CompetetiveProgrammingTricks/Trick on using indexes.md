se noi volessimo escludere un certo valore da una matrice o un [[Array]] data in input possiamo usare questo trucco: 

*ad-esmpio*: escludi la lettera maiuscola e minuscola di A da un dato array e stampa l'output: 

```c 
#include <stdio.h>
#include <stdlib.h>

int main(){
char daEscludere[101];
int i, l;
l = strlen(daEscludere);
for(i=0; i<l; i++){
	if(daEscludere[i]!= 'a' && daEscludere[i]!='A'){
	printf("%c", daEscludere[i]);
	}
}
}
```

la spiegazione dalla parte che non ho capito subito e questa:
```c
if((daEscludere[i]!= 'a')){/*da valutare*/}
```

se l'indice che viene dal input è ad esempio `*"e", "r", "s"*` **NON** è uguale ad `"a"` è la valutazione è vera (dato che non sono uguali) è l'if può proseguire nella iterazione del ciclo stampando l'output di quel indice, altrimenti quando si incontra l'indice *'a'* l'if diventa false è NON stampa l'output.

semplice no ? 

![[Pasted image 20221207152916.png]]

### Tags
#Cool_trick 
#Competetive_Programming 
#Codeforces