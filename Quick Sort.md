# Quick sort
è il modo più veloce per ordinari elementi in una lista 

possiamo invocarla in un programma usando questo prototipo che è derivato da `stdlib.h`

```c 
qsort(LaLista, NumeroElementiNellaLista, sizeof(int/*o altro*/), FunzConfronta);
```

FunzConfronta la conosco da [[Const Void]] ed è questa:

```c
int Confronta(const void *x, const void *y){
	return  *(int*)x -  *(int*)y ;
}
```


#Algorithms 

