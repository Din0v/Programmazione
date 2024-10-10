## Bitwise Operators.

- They look like the Logical Operators, the only difference that the operate on bits (not on the tits :p)

- one Major use of bitwise AND ```&``` and the bitwise OR ```|```  is in operations tp test and set individual bits in an integer value.  


![[Pasted image 20210218152209.png]]

Example:

```c 
#include <stdio.h>

int main(){
	unsigned int a = 60;  // 0011 1100
	unsigned int b = 13; // 0000 1101
	int result = 0;
	
	result = a & b;
	// the result is 0000 1100 that will be displayed in decimal. 
	printf("result is %d", result);
	
	
	return 0;
}
	
```

---
### Tags 
#Bitwise 
#Logical_Operators