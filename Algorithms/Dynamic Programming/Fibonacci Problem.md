# Fibonacci sequences using [[Recursion]].

Its solution is Recursive in nature.
[[Recursion]] and belongs to the family of [[Dynamic Programming]] Algorithms.

n =         1,		 2, 	3,		4,		5,		 7, 		8,		 9...
==Fib(n)== 1, 1, 2, 3, 5 , 8, 13, 21, 34;....


```js
const fib =(n) =>{
	if (n <= 2) return 1;
	return fib(n-1) + fib(n-2);
}; 
```

we need to visualize what the soution is by drawing a graph.
like the following:
we consider the number **7** as our input thus we get:

![[Pasted image 20201219215439.png]] 

It's an [[Asymmetric Graph]]

[[Childere value]] in a graph

[[Time Complexity]] is  in the [[Big O Notation]]
O(n) = 2<sup>n
	
