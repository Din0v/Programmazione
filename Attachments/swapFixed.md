``` c
#include <stdio.h>

//Funzione per lo scambio. 
void swap (int *a, int *b){   // un puntatore a una variabile a e b di tipo int
    
  
    int  temp; 
    temp = *a; // tmp conterrà il contenuto della variabile intera puntata da a
    *a = *b; // a conterrà il contenuto della variabile intera puntata da b 
    *b = temp; // conterrà il contenuto della variabile intera puntata da temp.  
   
   
}

int main () {

    int  a = 4; 
    int  b = 3;
    
    printf(" a=%d, b=%d\n ", a,b);
    printf("a & b lives at a: %p\t b: %p\n", &a, &b);
    swap(&a,&b); // Non passo le variabili alla funzione MA i loro indirizzi in memoria. 
    printf(" a=%d, b=%d\n ", a,b);
    printf("a & b lives at a: %p\t b: %p\n", &a, &b);
    
    return 0; 
    
 }
```

esercizio in come fare un scambio del valore di una variabile usando i [[Puntatori]] 

### Tags
[[Pointers]]
#Exercises 
#Basics 
#Cool_trick 