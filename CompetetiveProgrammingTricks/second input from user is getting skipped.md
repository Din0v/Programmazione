# Trick to solve skipping of multiple input from user:
check this example
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(){
    int n,len,i ; 
    char s[52];
    scanf("%d", &n); // the \n doesn't let this program skip the second fgets!!!
    fgets(s, 52, stdin);
    // scanf("%d", &n);
    
    len = strlen(s);
    printf("%d\n", n);
    for(i = 0; i<len; i++){
        printf("%c", s[i]);
    }
    
}
```

![[Pasted image 20221209161244.png]]
as you can see from this example, the second fgets got skipped completly!!! 
hence we add the `\n` next line specifier in the first scanf to solve this issue!

![[Pasted image 20221209161451.png]]

as you can see this clearly solved the issue completely!!


### Tags
#Debugging 
#interesting_fact 
#Erros 
