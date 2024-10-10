# Un esempio di divisione interessante
che ho trovato risovlendo questo esmpio [qui](https://codeforces.com/problemset/problem/617/A)
la divisione può essere mappata nella realtà dal esmpio del elefante che vuole raggiungere la casa di suo amico distante da lui `n` passi 
l'elefante può fare uno dei seguenti passi lunghi ( 5 , 4 , 3 , 2 ,1) 
qunindi data la distanza qual è il minimo numero di passi che deve fare ? 

la soluzione e come segue :

```c 
#include <stdio.h>
int main(){
int n, i, sum = 0;

scanf("%d", &n);

	if(n%5==0){
		n = n / 5;
	}
	else{
		n= (n/5) +1;
	}
printf("%d", n);

}
```
come si nota che qualsiasi numero divisio 5 avra un resto strettamente inferiore di 5 ( per definizione della divisione ). 
è per questo motivo che si aggiunge al **RISULTATO** della divisione 1 dato he questo passo sarà fra uno di questi numeri: (4, 3, 2 ,1) ed richederà un ultimo passo per il nostro amico elefante!!

### Tags

#implementazione
#Cool_trick 
