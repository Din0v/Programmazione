# Come allocare dinamicamente le dimensioni di una matrice ? 

```c 
int main(){
	int size, i;
	scanf("%d", &size);
	double* matrix;
	
	matrix = (double*)malloc(size* sizeof(double));
	
	for(i=0; i<size; i++){
	scanf("%lf",&matrix[i]);

}
```

### Tags 

#Arrays
#Math 
#implementazione 
