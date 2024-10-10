il problema si trova [Qui](https://codeforces.com/problemset/problem/492/B) che è un problema di matematica + [[Ricerca binaria]]. ( potrebbe essere risolta con la ricerca binaria!)
abbiamo utlizzato il [[Selection Sort]] per ordinare la liste di lampade di input!

>Premi $$ctrl \ + \ shift \ + v$$ to paste while mainting source format!!

Codice: 
```c 
/*CF problem Vanya and lanterns found here:
https://codeforces.com/problemset/problem/492/B
cosa ho imparato ?
*/

#include <stdio.h> 

int main(){
    int n, l;
    scanf("%d %d ", &n, &l);

    double lantern[1001];

    int i, j; 
    for(i=0; i<n; i++){
        scanf("%lf", &lantern[i]);
    }
	// selection sort!!
    int temp;
    for(i=0; i<n-1; i++){
        for(j=i+1; j<n; j++){
            
            if(lantern[j]<lantern[i]){
                temp = lantern[i];
                lantern[i] = lantern[j];
                lantern[j] = temp; 
            }
        }
    }

    // for (i = 0; i<n; i++){
    //     printf("%f ", lantern[i]);
    // }

    double w, d = lantern[0] - 0;

    for(i=0; i<n-1; i++){ // sempre meno 1 dato che l'indece parte da zero
        w = (lantern[i+1] - lantern[i])/2;
        if(w>d)
            d = w;
    }

    if((l - lantern[n-1])>d){
        d = l - lantern[n-1];
    }
    printf("%f", d);

}
```

1. Prendiamo l'input da come chiesto nel problema sovvracitato. con scanf che punta la indirizzo di $n$ ed $l$ respettivamente. 
2. viene definita una matrice del tipo double dato che la precisione richiesta nel esercizio è di $10^9$. vedasi: [[Difference between Double and Float]]
3. si prende l'input della matrice;  scorrendo l'indice con un ciclo for.
4. poi si effettua la ricerca binaria:
	1. si definisce un intero temporaneo $temp$
	2. si definiscono due cicli anndiati for. dove si confrontano i primi due indici adiacenti $i=0$ ed $j=i+1$ si fissa il primo ( con il for esterno ), poi si scorre il ( for interno ).
	3. se la valutazione del if fallisce ovvero si ha che dentro l'indice fissato è maggiore de quelo che viene confrontato si fa l'operazione di $swapping$ 
5. si determina il modo con cui calcolare il diametro della luce con il valore del indice 0 meno 0 ( il punto di partenza della strada) 
6. si definisce la variable $w$ che accerta che il valore massimo del diamatro sia giusto






### Tags
#SavoirFaire 
#interesting_fact 