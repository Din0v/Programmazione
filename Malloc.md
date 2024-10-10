# Memory Allocation 
nasce nel contesto che nel mondo reale spesso non possiamo prevedere la dimensione di un array durante la progettazione del codice 

**malloc** pende un parametro che dovrebbe essere ovio, ciò ( qunata dimensione vuoi allocare caro mio programmatore ?? )

la risposta usa ( *sizeof (tipo di dato )* x (dimensione di un array))

esempio: 

```c 
int *ArrayRiverso = (int*) malloc(sizeof (int) * dimensione);

```
malloc assomiglia molto a [[Calloc]] 

bisogna sempre liberare la memoria dalla allocazione inutilizata dato che la situazione si può aggravare in un [[memory leakeage]].

### Tags
[[Array]]
[[Pointers]]
[[Functions]]
