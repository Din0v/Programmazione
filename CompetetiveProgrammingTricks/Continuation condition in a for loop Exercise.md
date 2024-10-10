# Very informative Continuation condition use Case in a for loop 

vedi ->[[Loop]]s

ho incontrato questo modo di fare risolvendo il problema [732A in codeforces](https://codeforces.com/problemset/problem/732/A)

il codice:
```c
#include <stdio.h>
int main() {
  int n,r,i;
  scanf("%d %d", &n, &r);
  for(i=1;i<=10 && i*n%10!=0 && i*n%10!=r; i++);
  printf("%d\n", i);
```

here we manipulated the condition of the loop so that it can take additional arguments using the "AND" logic hence the loop will NOT PRINT ANYTHING.

>[!warning]
>ATTENZIONE: PUNTO VIRGOLA DOPO IL FOR

>[!Warning]
>ATTENTION ABOUT THE SEMICOMMA AFTER THE FOR LOOP     

1. $i$ is smaller than or equal to 10

 2. if the $i th$ element multiplied by n modulo 10( for the last digit doesn't equal zero)

```
the example is from the first input  ==>>(117 3)

example: 117 x 1 = 117 ==>>117  % 10 = 7 which isn't zero!!
```
   
3. if the $i th$ element multiplied by 10 modulo 10 doesn't equal the remainder given by the original problem. 

```
example: 117 x 9 = 1153 ==>> 1153 % 10  == 3 which equals the Given remainder.
```    

Little Note on why we didn't use the == and instead we used the != it's similar to a not gate, 
or for when we put a transistor on a gpio pin so the logic gets invertered.

here is my simple explanation:  
        - since the loop will only print once the evaluation can be more intricate.
        - so if the term t NON è UGUALE  allora di conseguenza NON STAMPARE!!
        - if it isn't equal DON'T Print ANYTHING!!
        - 1153%10 != 0  ==>>> TRUE
        - 1153%10 != r(3) ===>>> FALSE
        - (117x3) = 351 ==>> 351%10  != r(3) ==>> TRUE 

we call the arguments in the continuation condition after the && "**FLAGS**" and they have to be true !!



### Tags
#Codeforces 
#Competetive_Programming 
#Cool_trick 
#implementazione 
#IMPORTANT
