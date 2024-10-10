# Come fare con i numeri incredibilmente grandi

usare python per calcoli numerici è molto più facile che usare C :) 

questa qui è una domanda che ho incontrato su [HackerRank](https://www.hackerrank.com/challenges/extra-long-factorials/problem)

questo è modo per calcolare fattoriali grandissimi come  
```45!``` 

in C esiste una libreria che si chiama ```gmp.h```

```python 
#!/bin/python3
import math
import os
import re
import sys
from decimal import Decimal, getcontext
import random

def extraLongFactorials(n):
    getcontext().prec = n + 90
# Set precision to a value greater than n
# Use Decimal for increased precision
    result = Decimal(1)
    for i in range(2, n + 1):
        result *= Decimal(i)

    return result

if __name__ == '__main__':
    
    k= extraLongFactorials(45)
    
    print(k)
```



---
### Tags 
#Algorithms 
