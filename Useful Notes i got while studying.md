# Useful Notes. 

1. it's important to inizialize a summing variable with 0 because otherWise we would be getting values all over the place just like with this example 

```c 

# include <stdio.h>

int main() {

	int i, n;
	int sum = 0; // è importante inizalizzare la variabile sum con il 0 perchè altrimenti da risultati errarti.
	
	printf("enter the input\n");
	scanf("%d", &n);
	for(i = 1 ; i <= n; i++){
		printf(" %d", i );
		sum = sum + i;
	}
	
	printf("\n");
	
	printf(" the sum is: %d", sum);
	printf("\n");
	printf(" q has this value: %d", q); // solamente per capire che le variabili sono inizializzate con valori a casaccio. 


}

```

if i don't make the sum = 0 the results would be like this. 
![[Pasted image 20211027133531.png]]

when adjusted like the above example we get the correct answer: 
![[Pasted image 20211027133600.png]]

18 Maggio 2022,
sembra che gcc non importa più questo aspetto ?? 
compila correttamente in entrambi i casi ?


### Tags 
#interesting_fact 
#Debugging 
#Exercises 