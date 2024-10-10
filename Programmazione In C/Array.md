# Array 
Una sequenza contigua(Neighboring) **(valori, oggetti, informazioni)** dello *stesso tipo*, inoltre sono correlati ai [[Puntatori]].

### Le proprietà delle array:
1. hanno una dimensione fissa in quanti elementi essa contiene. viene definita al momento della creazione dell'array e non è modificabile durante l'escuzione. 
2. tutti gli elementi del array hanno lo stesso ==tipo==
3. gli elementi sono memorizzati in *locazioni contigue* di memoria [[Array flatteing]]
4. accedere ad un elemento del array richiede tempo costante, indipendentemente dalla sua posizione. 

l'array si creano in questo modo: 
```c 
int Un_array[10]; // un array di undici elementi
```

NB. 
è utile assumere che un  [[Array]] o una variabile ==Non esplicitamente== inizializzato contega valori casuali. 

--- 
>[!warning]
>le due espressioni, hanno lo stesso significato:

```C
				a[i];      *(a + i);								
```


Interessante come Relazione: 

![[Pasted image 20220926143857.png]]

Vedi anche questa e provala: 

![[Pasted image 20220926144422.png]]------
it's a good practice to initialize all arrays to $0$ when in a declaration:
```c 
array[10]={0}
```
#interesting_fact 

- it's Kosher to access an array in this way:
```c 
int Array[] = {1, 2, ,3, 4, ,5};
printf("%d\n" 3[Array]); // è un modo per accedere al 4° elemento del array.
```
---
- An array variable can b used as a pointer.
- 

---
### Tags 
#Basics

