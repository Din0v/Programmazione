breve epifania nella mia auto spiegazione.
## Caso 1
vuoi modificare il valore iniziale della variabile passata ? 
se si; allora la funzione deve ricevere un puntatore 
e tu devi passare l'indirizzo della variabile !!

```c 
# include <stdio.h>
void inc(int *v) {
	*v = *v + 1;
 }

int main() {
	int x = 0;
	inc(&x);
	printf("%d\n", x );
return 0;
}
```
la funzione inc modifica direttamente la variabile x nella main, appunto perchè abbiamo passato alla funzione il indirizzo della variabile x e la funzion prende un **PUNTATORE** in input e non restituisce ninete dato che va a manipolare direttamente la variabile x 

## caso 2

esempio due senza puntatori ( con risultati diversi):
Vuoi lasciare il valore iniziale intatto (vergine maria) ?
ecco devi fare cosi passi **UNA COPPIA** e poi la funzione restituisce una altro parametro

```c
#include <stdio.h>
int inc(int x){
	x = x + 1;
	return x;
}

int main(){
	int x = 0;
	inc(x);
	printf("%d\n", x );
	printf("%d\n", inc(x))
return 0; 
}
```

il risultato: 
![[Pasted image 20221217173240.png]]

vedi per aver il risultato di x, ho invocato la funzione (*en sa splendeur*) 
mentre x è rimasto invariato!!

### Tags
#Basics 
#Exercises 
#implementazione 
#
[[Puntatori]]
[[Functions]]