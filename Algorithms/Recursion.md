# La Ricorsione

## Definizione:

è un algoritmo che si esprime in termini di se stesso, ovvero in cui l'esecuzione dell'algoritmo su un insieme di dati comporta la semplificazione o suddivisione dell'insieme di dati e l'applicazione dello stesso algoritmo agli insiemi di dati semplificati.


### Example 1

```Js
Const foo = (n) => {
	if (n <= 1) return;
	foo(n-1);
};
```

![[Pasted image 20201219222914.png]]

we have 5 recursive Calls which resullts in:
==O(n) time==
==O(n) Space==

![[Pasted image 20201219223033.png]]

In analaizing the [[Space Complexity]] of our recursive functions we shoud include all of our [[Stack base]] f the function call makeup.


### Example 2

```js
const bar = (n) => {
	if (n <= 1) return;
	bar (n - 2);
};
```

It's very similar to the first example 

![[Pasted image 20201219224637.png]]

we are doing the recusive call in 2 steps at a time which in turn makes the Big O natation $\frac {n} 2$

![[Pasted image 20201219224753.png]]

but taking out the constants we get the same value for the time and space complexity as example 1 
Hence

==O(n) time==
==O(n) Space==


### Example 3

```js
const dib  = (n) => {
	if (n <= 1) return;
	dib (n - 1);
	dib (n - 1);
};
```

let's take **5** as an example and try to graph it

 5 is going to branch into two [[Childere value]]s as shown in this picture 
 
 
 ![[Pasted image 20201219230527.png]]
 
 we will try to leverage our past experience. 
 
 in this path highlighted in yellow we see the route going to the base case 
 it goes 5, 4, 3, 2, 1
 
 ![[Pasted image 20201219230623.png]]
 
 the length of this path is going to be **n** different nodes
 
 ![[Pasted image 20201219230813.png]]
 
 if we adapt the language of the tree we can say that the height of this tree is **n** as it's the distance from the ==Root Node== to the ==farthest Leaf==
 
 ![[Pasted image 20201219231040.png]]

we can also say that the  ==Number of Levels== is also **n**

![[Pasted image 20201219231159.png]]

![[Pasted image 20201219231226.png]]

On the first level there is 1 node
On the second level there are 2 nodes
On the third level there are 4 nodes
On the fourth level there are 8 nodes
On the fifth level there are 16 nodes

See a pattern here ??

Formalizing:
no matter what in the ==dib== function the top level node is always going to be 1 the next is going to be x2 the third is the previous one x2 and so on as shown here 

![[Pasted image 20201220000047.png]]

in Conclusion we are saying that to get the total number of nodes  (Recursive calls) we take the number 2 and multiply it **n** times over 
and this is really the defenition of an exponent 
O($2^n$)

a recursive process is composed of $winding$ and $unwinding$.

the $winding$ terminates when it reaches it $terminating \ condition$ il *caso base*.

![[Pasted image 20220926151712.png]]

![[Pasted image 20220926155134.png]]

Esempio Ricorsivo in C 
```c
/*soluzione ricorsiva della somma di N numeri naturali*/

#include <stdio.h>
int sum(int n){
    if(n>0) return n + sum(n-1);
    else return 0;
}
void main (){
    printf("%d", sum(12345));
}
```

---
### Tags 
#Algorithms 
[[Fibonacci Problem]]
#Fibonacci
#Recursion
