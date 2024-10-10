# Interesting Ternary operator use

i stumbled upon it while solving *problem* $581$ in codeforces [here](https://codeforces.com/problemset/problem/581/A).

so it goes like this:
```c 
# include <stdio.h>
# include <math.h>
int a,b;
int main(){
	scanf("%d%d",&a,&b);
	printf("%d %d",a<b?a:b,abs(a-b)/2);
}
```
## Spiegazione: 
1. la prima cosa che noto è la compattezza del codice rispetto alla mia implementazione 
2. è il uso maestroso del valore assolute $abs$ per non valutare un ulteriore condizione. 
3. l'uso del [[Operators]] ternario $?:$ che funziona come segue: 
	1. prende tre operandi nel nostro caso: $a<b$, $a$ ed infine $b$ 
	2. segue una logica sequenziale nella valutazione 
	3. se la condizione definita come $a<b$ è vera allora stampera $a$
	4. altrimenti ( che è la condizione dopo i due punti $:$ ) stampera $b$

![[Pasted image 20230104130708.png]]

### Tags 
#Competetive_Programming 
#Codeforces 
#Operands 
#interesting_fact 
#implementazione 
#Cool_trick 
