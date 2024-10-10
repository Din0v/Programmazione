here are the two standard and straight forward way to iterate over [[Array]] in C:

## Adding elements to an array via scanf:

```c 
int p[5], i;
for(i=0; i<(5-1); i++)
	scanf("%d", &p[i]);
```

vedasi l'indirizzo del puntatore **&p[i]**. 

## Reading the elements of an array using printf:

```c 
int i, p[] = {1, 2, 3, 4, 5}; 
for(i=0; i<(5); i++)
	printf("%d, " p[i]);
```

attenzione alla disequazione, nel esempio precenente l'iterazione avviene strettamente per gli elemente **MINORI** di 5 quindi non serve sotrarre 1 dalla argomento del _for_. 

l'inizializzazione di un array richiede paretesi **GRAFFE**, "{"

il motivo per cui le array cominciano da 0 [Bella Lettura](https://albertkoz.com/why-does-array-start-with-index-0-65ffc07cbce8)
we should consider the `v[i]` the `i` is in fact an offset of memory!!

### Tags
#SavoirFaire
#C_CookBook
