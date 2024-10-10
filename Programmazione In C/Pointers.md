# Pointers 

[Infromative video](https://www.youtube.com/watch?v=2ybLD6_2gKM)

for some reason instructors create hype around them and phobia mongoring, mah

**Pointers:** is just the address of a piece of data in memory. 

pointers allow you to:
1. avoid copies 
2. work on the same peice of data, "Share Data"

It's called a *Pointer* because it **Points** to a [[Variables]] in memory.

The unary operator **&** gives the address of an object.

the unary operator ** (*)Asterisk ** is the indirection or **derefrencing** operator, when applied to a pointer it accesses the objects that the pointer points to!

A **Pointer variable** is just a variable that stores a memory address. 

``` c 
			int *address_of_x = &x; 
		
```

here we can see that the variable **address_of_x** is assigned to the variable **x**. 


> Q: can i create a float pointer variable for the address of the pointer ?
>  arguments are stored as int* in functions
>   

pointers consist in __ parts

1. the usage of ``` & ``` to find the address of the pointer (this finds the address of the pointer)
2. the usage of ``` * ``` to set the address of the pointer (This reads the value of the pointer)
3. 

Pointers allow for complex data structures such as   [[Linked lists]] and [[Binary trees]]

##  Intresting remark for my understanding:

Many turorials declare pointers like this 
```c
	int *x;
```

and others do it this way:
```c
	int* x;
```

the first is the most common which is annoying.
because the second makes much more sense, when i read int *x here is an int and it's name is "*x", which isn't quite right!!! 

but when i read the second i see here is  an *int pointer* and it's name is x which is pretty accurate!

both have the same exact meaning to the compiler.

but one argument in favor of the first version is prefereable because it will result in the following problem:

```c
	int* x,y,z ;
```

```c
	int *x, y, z;
```

it implies that x, y, and z are all pointers, which they are not!! ( only x is )

if i used the first syntax there wouldn't be a problem as it will be pretty clear that *x is the only pointer of the bunch. 

but if i don't go mixing declarations all over the place this shouldn't be a problem. 

so i declare pointers and variables seperately. 

>[!Warning]
> Ma compili ??

YES IT DOES WORK

--- 
### quick tips

C sends **arguments** as *values*!

Pointers make it easier to share memory 

**Dangling Pointers:** are pointers that point to invalid addresses.



### Tags
#Basics 
