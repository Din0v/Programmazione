# I Puntatori 

[[Pointers]]

siccome non ho capito profondamente da questo :

![[Pointers]]

provo a spiegare a me stesso in Italiano!!
 
 ``` c 
 
 int a = 4; // è una semplicissima dichiarazione di una variabile 
 
 int *x; // un "puntatore" a una variabile x di tipo int 
 
 x = &a; // il puntatore "x" contiene l'indirizzo della vairaibile "a"
 
 *x = 4 /** in questo modo modifico il contenuto del valore puntato da x, quindi modifico indirettamente il valore di a */
 
 ```
 
 **&a**: identifica l'indirizzo in memoria al quale si trova la variabile **a**. questo indirizzo viene salvato nel puntatore x.


here we got another example:
![[swapFixed.c]]



--- 
## Tags
[[Pointers]]


