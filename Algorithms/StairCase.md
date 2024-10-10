# La funzione delle scale
```c 
supponiamo che n=5; volgiamo una scale di questo tipo

a = [ * * * * # 
	  * * * # #
	  * * # # #
	  * # # # #
-	  # # # # # ]
```

```c
/*StairCase function using #*/

#include <stdio.h>

void printStaircase(int n) {
    // outer loops controls the hight of the stair 
    for (int i = 1; i <= n; i++) {
        // Print spaces
         for (int j = 1; j <= n - i; j++) {
            printf("*");
        }
// l'ordine in cui vengono eseguiti questi cicli è importante!!!
        // Print '#' for the steps
         for (int k = 1; k <= i; k++) {
            printf("#");
        }

        // Move to the next line after printing each step
        printf("\n");
    }
}

int main() {
    int height;

    // Get the height of the staircase from the user
    printf("Enter the height of the staircase: ");
    scanf("%d", &height);

    // Call the function to print the staircase
    printStaircase(height);

    return 0;
}

```

il trucco sta nelle tre matrici annidate: 

1. Il primo ciclo: 
```c
for (int i = 1; i <= n; i++) 
```
**controlla** l'altezza delle scale. 

2. Il secondo ciclo: 
```c
for (int j = 1; j <= n - i; j++)
```
riempe i spazi vuoti della matrice. supponiamo che ```n=5``` allora nel primo passaggio il ciclo dovrà saltare ```n-i = 5-1 = 4``` spazi dunque nella prima riga sono disegnati 4 spazi!

3. Il terzo ciclo:
```c
for (int k = 1; k <= i; k++)
```
il ciclo viene eseguito dopo quello precedente e dunque il cursore sarà arrivato al punto in cui bisogna terminare la "matrice" con i elementi mancanti che saranno uguali ad ```i = k``` possiamo chiamarle questo ciclo ==Ciclo del Complemento==



--- 

### Tags 
#Algorithms 

 