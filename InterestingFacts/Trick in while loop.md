# While loop while decrementing a variable:

check this out: 
while solving the codeforces problem 69A [here](https://codeforces.com/problemset/problem/69/A) i found a peculiar way to use a while [[Loop]]:
```c
int n = 5;
while(n--){
	scanf("%d %d %d", &x, &y, &z);
	sumX = sumX + x;
	sumY = sumY + y;
	sumZ = sumZ + z;
}
```
the `n--` it runs the loop until `n` hits 0 which is *logically* equivalent to false.

![[Pasted image 20221212004453.png]]

#Cool_trick 
#interesting_fact 
