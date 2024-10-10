# scanset
>[!warning]
>*why you shouldn't use gets*
>what should you do instead:
>USE A SCANSET!!!!

a scanset is a way to tell the [[scanf]] [[Functions]] where to stop.
at what input charachter should it stop taking input!!
```c
#include <stdio.h>
 int main(void)
{
    char str[128];
    printf("Enter a string: ");
    scanf("%[A-Z]s", str);
 
    printf("You entered: %s\n", str);
 
    return 0;
}
```
in the previous example the scanf will scan all the capital letters and ommit the rest of the characters!

```c 
scanf("%[^\n]s", str2);
```
in this example it will scan all the charachters until it meets the (next line) ( pressing enter!)

```c
scanf("%[^o]s", str3);
```
it will stop scanning after the first occurence of the letter O

it's much better to use this format than using the **Gets** function!!

#Basics 
#interesting_fact 
#Debugging 
#overFlow