Imparato sta tattica da codeForces Esempio: 217A.c ( vedi i esercizi..).

supponiamo che vogliamo continuare a incrementare un valore a finché non si soddisfi una condizione; 
ci viene spontanea utilizzare la forma:

```c 
while(1)
	// fa qualcosa 
	// il qualcosa è soddisfatto 
	break;
```
questa forma funziona ma non è elegante dato che è difficilmente mantinibile in iterazioni future.  

la forma migliore da utilizzare è la seguente: 

```c 
do{ 
// qualcosa
}while(!(/*questa condizione*/));
```

si legge come segue: 
fai questa operazione per ALMENO UNA VOLTA e se la condizione nelle parentesi è soddisfatta ( doppia negazione )

l'esempio:
```c
# include <stdio.h>
int main(){
    int n, a, b, c, d;
    scanf("%d", &n);
    do{
        n = n+1;
        a = n / 1000;
        b = (n / 100) % 10;
        c = (n / 10) % 10;
        d = n % 10;

    } while(!(a != b && a != c && a != d && b != c && b != d && c != d));
    printf("%d", n);
}
```

```
la condizione con i or è soddisfatta ?
No; allora falso X falso = il while rimane true 
la la condizione con i or è soddisfatta ?
Si: allora vero X falso == FALSO !!
e per cio termina l'esecuzione!

```

### Tags
#Codeforces 
#Cool_trick 
#BestPractice
#Exercises 
[[Loop]]
[[While]]


