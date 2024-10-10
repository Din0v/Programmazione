# Casting in C 

A cast in C is only meaningful at compile time becasue it tells the [[Compilers]] how you want to manipulate a piece of data, it doesn't change the actual value of the data.
for example: 

an ``` (int*)p ``` tells the compiler to treat P as a memory address to integer. 
and this operation costs nothing at run time, the processor just deals with raw numbers the way they are given to it. 

usando il casting il programmatore dimostra al compilatore che è consapevole di ciò che sta facendo. 

Esempio: 

```c 
int x = 7;
int y = 2;

float z = (float)x / (float)y;
printf("z = %0.f", z);

```

here we only told the compiler what values "we expect" hence it's called casting!
