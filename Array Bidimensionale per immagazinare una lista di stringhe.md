ho incontrato questo modo di risoluzione mentre stavo risolvendo il problema  [785B](https://codeforces.com/problemset/problem/785/A) mi serviva un modo per indirizzare diverse stringhe distinte ma tutte immagazinate in un array; 

e si fa cosi:

```c 
char hedron[5][12] = {"Tetrahedron", "Cube", "Octahedron" , "Dodecahedron", "Icosahedron"};

for (int i = 0; i < 5; i++) {
    printf("%s\n", hedron[i]);
}
```

si definisce una array bidimensionale:
1. Le prime parentesi quadre definiscono il numero degli elementi che vogliamo immagazinare.
2. Le scende parentesi quadre definiscono il numero di caratteri massimo nella stringha data in input.


### Tags 
[[Array]]
#Cool_trick 
#Codeforces 
