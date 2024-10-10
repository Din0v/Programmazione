
the `?:`  operator is used as follows:
![[Pasted image 20221014101619.png]]
### Example: 

```c 
/** i get to learn the ?: operator*/
# include <stdio.h>
int Triple(int a, int b){
	int t;
		if (a == b){
			t = (a + b)*3 ;
		}
		else{
			t = (a + b);
		}	
	return t ;
}

int AnotherImplementation(int x, int y){
	return x == y ? (x + y)*3 : (x + y) ;
}

  

int main(){

	printf("sum of a and b is %d\n", Triple(5, 5));
	printf("sum of x and y is %d\n", AnotherImplementation(4,4));

}

  

// this is a neat trick
```

### Tags
#Basics #Cool_trick 

