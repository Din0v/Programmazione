
# Acronyms 
---
**Atoi** == ascii to integer 

---
**Atof** == ascii to float
```c
	#include <ctype.h>

// atoi convert s to integer; version 2 

int atoi (char s[])
{

    int i, n, sign;
    
    for (i = 0; isspace(s[i]); i++) // skip white space , the isspace is defined in the ctype header
    sign = (s[i] == '-') ? -1 : 1;
    if (s[i] == '+' || s[i] == '-') /*skip sign*/ 
    i++;
    for (n = 0; isdigit(s[i]); i++) // the isdigit is defined in the ctype header!!
        n = 10 * n + (s[i] - '0'); 
     
     return sign * n; 
     
 }
```
as we can see the second argument "expr2" the the *isspace* is the relational expression defined in the header the <ctype.h> 

---

**Itoa** == integer to ascii


---
**ftoa** == float to ascii 

 