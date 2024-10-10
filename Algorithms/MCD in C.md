# Massimo Commun Divisore in C

questa è una implementazione del algoritmo di euclide MCD scritta in C:

## 1. Algoritmo Ricorsivo:
```c
int MCD(int a, int b){
	if(b == 0)
		return a;
	else
		return MCD(b, (a%b));
}
```

## 2. Algoritmo iterativo:
```c
int MCD(int a, int b){
	int temp;
	while(b!=0){
		temp = a%b;
		a=b;
		b= temp;
	}
}
```



### Tags
#Algorithms 
#Recursion 