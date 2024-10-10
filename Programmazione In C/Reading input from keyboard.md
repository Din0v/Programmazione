# HID human input device.

- it's useful to ask the user for input (such as a keyboard).

- the ``` scanf ``` function uses [[Pointers]] to [[C Variables]]


### The 3 Rules about ```scanf```:

1. it returns the number of items that it successfully reads
2. if you use ```scanf``` to read a value for one of the basic [[C Variables]] types, preccede the variable name with ```&``` 
3. if you use ```scanf``` to read a string into a character array don't use ```&``` 



#### Example:
```c

int main(){
	
	double gpa;
	int age;
	printf("Enter your age");
	scanf("%d", &age):
	printf("Enter your gpa:");
	scanf("%lf", &gpa);
	printf("Your gpa is %f", gpa);
	
return 0;
}
```

Using scanf is a pwoerful tool. 

we can use ```fgets``` to take a string of charcters, 

```C 
char name[20]
fgets(name, 10, stdin);
```
