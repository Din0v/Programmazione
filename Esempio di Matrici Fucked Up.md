```c
#include <stdio.h>

int main() {
	int matrice[2][3] = {1,2,3,4,5,6};
	int* m = (int*) &(matrice[0][0]);
	printf("%d %d\n", m[0], matrice[0][0]);
	printf("%d %d\n", m[1], matrice[0][1]);
	printf("%d %d\n", m[2], matrice[0][2]);
	printf("%d %d\n", m[3], matrice[1][0]);
	printf("%d %d\n", m[4], matrice[1][1]);
	printf("%d %d\n", m[5], matrice[1][2]);
return 0;
}
```

un altro esempio leggermente più chiaro è questo:

```c
int main(){
    char Matrice[3][4] = {"ciao", "Derp", "MEEH"};
    // stessa logica per il int;
    int ArrNumeri[3][3] = {1, 2, 3, 4, 5 ,6 ,7 ,8, 9};
 
printf("%c\n", Matrice[2][0]);  // dovrebbe restituire M 
printf("%d\n", ArrNumeri[2][1]); // dovrebbe restituire 8 !!
}

```

nella dichiarzione si scrive **LA DIMENSIONE EFFETTIVA**.

nel uso si utilizza la posizione del elemento nel array, ed e questa cosa che mi ha confuso leggermente. 

si possono organizzare le array in doppiette e triplette appunto come nel esempio $Matrice$ di prima, li abbiamo $3$ parole, ed ogni parola ha una dimensione di $4$. 



