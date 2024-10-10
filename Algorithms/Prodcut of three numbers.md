# come trovare se un numero N è composto dal prodotto di 3 numeri  distiniti: 

ho incontrato questo problema risolvendo: [1294C](https://codeforces.com/problemset/problem/1294/C) vedi gli esercizi!!

*Soluzione algoritimica:* 
To determine if a number n can be expressed as the product of three distinct numbers, you can follow these steps:

1. Find the prime factorization of n: Decompose the number n into its prime factors. This can be done by dividing n by prime numbers starting from 2 and continuing until n is reduced to 1. (usando la funzione)
```c
findPrimeFactors(int n) // vedi folder AUX functions
```

2. Count the distinct prime factors: Once you have the prime factorization of n, count the number of distinct prime factors. If there are fewer than three distinct prime factors, it means that n cannot be expressed as the product of three distinct numbers.

3. Check if the exponent of each prime factor is 1: If n has three or more distinct prime factors, check that the exponent (the power to which each prime factor is raised) for each prime factor is exactly 1. If any of the prime factors have an exponent greater than 1, it means that n cannot be expressed as the product of three distinct numbers.

4. Confirm that n is not a perfect cube: If n passes the previous steps, ensure that it is not a perfect cube. A perfect cube is a number that can be expressed as the cube of an integer. If n is a perfect cube, it cannot be expressed as the product of three distinct numbers.