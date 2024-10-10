# manipulation of the exit condition to excute other programs 

```c 
#include <unistd.h>

int main (){
    char c;
    while (read(STDIN_FILENO, &c, 1) == 1 && c != 'q'); // the q is for quitting condition 
    return 0; 
}
```

the cute thing is anything that i type after the exist the letter ==q== i can type and actual command that will excute automatically be it like 

> this progam will excute q cpufetch 

![[Pasted image 20210831124905.png]]

so basically from a text editor to an exploit that excutes cpufetch ?? cool !! 


### Tags
#interesting_fact 
#kilo 
