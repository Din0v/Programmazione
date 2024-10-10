# La Notazione Posizionale 

è una cosa molto comune da utilizzare, che ho incontrato diverse volte risolvendo i problemi su CF ad esempio [qui](https://codeforces.com/problemset/problem/313/A)
come esprimere la notazione posizionale di un numero programmaticamente: 

supponiamo di avere il numero:$$- 123$$
si potrebbe fare così:
```c 
int n; 
n/10; // si eliminerebbe la posizione di 3 (dato che è un int)
```

nel esempio di prima si eliminerebbe la posizione di 3 (dato che è un int) ed il risulatao sarà $$ -12 $$
se noi volessimo eleminare il $2$ dal $123$ si potrebbe fare così: 
```c 
int n;
(n%10) + (n/100)*10;
```

nel prima parte del equazione si isola il primo numero che è $-3$  e si aggiunge a $10$ ma come possiamo ottenere il numero $10$ ? 
usando la seconda parte dell'equazione: 
prima si divide il numero per $100$ ottenedo $-1$ e poi appunto si moltiplica per 10 dato che a noi ci interessa SOLO la posizione, ma non il valore contentuto coiè $1 \times 10^1$ oppure  nella posizione $2$ metti $0$ 
e poi si sommano i due operandi ottendo $-13$ che è sostanzialmente come eleminare 2 dalla **posizione** 2

--- 
## Un altro modo per esprimere questo concetto 

il modulo di un numero e come andare ad eleminare il $$10^x$$nella rapresentazione Posizionale del numero!! ottentndo solamente il valore moltiplicato per esso.
*dove $x$ è un numero Naturale.* 
ad esempio:
$$ 12 = (10^0 \times 2) \: + \: (10^1 \times 1) $$
usando il modulo si isola la prima posizione notazionale.
$$12\%10 = 2 $$ 
usando la divisione su 10 si isola la seconda posizione $$\frac{12}{10} = 1 $$
se utilizziamo un **int**

--- 




 ### Tags 
 #Codeforces 
 #Basics 
 #NumberTheory
 [[Sul Utilizzo di while]]
 [Wikipedia Notazione Posizionale](https://it.wikipedia.org/wiki/Sistema_di_numerazione_posizionale)
 