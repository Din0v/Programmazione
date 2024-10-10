it's the main reason that pointers have types!!!

cosi il compilatore sa quanto deve saltelare con la aritmetica dei [[Puntatori]]

ad esempio, 
***char*** salta di 1 **Byte** di memoria.
***int*** salta di 4 **Byte** di memoria.
e cosi via. 

```c
# include <stdio.h>

void skip(char *msg){
	puts(msg + 6);
}

int main(){
	char *msg_from_me = "Don't call me";
	skip(msg_from_me);
}
```

>[!Warning]
>puts means: Put string in Standard output!!

questo è un esempio sulla aritmetica dei puntatori dove (msg + 6) a *Shiftato* il puntatore di 7 posizioni. 

you can add and subtract in pointer arithmitic but you ==CAN'T== multiply. 

be aware that subtracting more thant the length of the array might result in a [[Segmentation fault]] or an [[Abort trap]]. and usually it's a hacking attack surface. 

---
### Tags 
#interesting_fact 
#Explainer 
[[Pointers]]
