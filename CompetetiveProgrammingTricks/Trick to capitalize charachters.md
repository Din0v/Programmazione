i discoverd this in CF  problem Nr. 118A
if we are asked to convert capital letters to small letters or vice versa, we can adopt the trick of adding or subtracting 32 from the ascii table seen here: 

```c 
if(s[i]<=90/*'Z'*/) s[i]+=32; 
//32 is ascii for "space", Oppure è la differenza ascii tra il maiuscolo o il minuscolo 
printf(".%c",s[i]); 
// adding something before the format specifier prints it out before each charachter, especially that we are here inside the loop!!
  }
```

here is the [[ASCII]] table in question 

i learend this trick resolving problem 118A.c in codeforces ( check your excercise files!!).

### Tags
#Cool_trick 
#Competetive_Programming
