# Enums. 

- Enumeration is a list of constant integer values as in
	``` c 	
	enum boolean { NO, YES } ;
	```

è un altro modo per creare variabili 
```c 
enum week{sun, mon, tue, wed, }

int main(){
	enum week day; // creazione di una variabile di tipo week nome day
	day = mon;
	printf("%d", day);
	return 0; 
}
```


---

## Tags
#Enums