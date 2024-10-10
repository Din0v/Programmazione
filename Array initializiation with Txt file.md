# Array initializiation with Txt file
here is a way to initialize an array from an external file:

```c
int main(){
int a[] = {
	#include "data.txt"
};
// then we loop through all of it to see the results
for (int i = 0; i < 10; i++){
	printf("a[%d] = %d\n", i, a[i]);
}
}
```


### Tags
#Arrays 
#Cool_trick 
