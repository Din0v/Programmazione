# Const Void
è un tipo a cui si puo' formare un puntatore 

prima volta l'ho incontrato nella funzione *confronta*

```c
int Confronta(const void *x, const void *y){
	return  *(int*)x -  *(int*)y ;
}
```

 [[Stdlib]] Da cui poi si ricava la funzione per il [[Quick Sort]]
 