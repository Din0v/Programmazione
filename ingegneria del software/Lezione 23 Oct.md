# Notes
1. cosa mi serve (documento delle specifiche )
2. ho il progettista (che mi dice come dove sviluppare)
3. viene passato a coloro che faranno l'implementazione 

block diagram --> sottosistemi --> le frecce mostrano le dipendenze 

caratteristiche del modello repository 

speculare è la relazione tra client-server e repository 

modello di condivisione dei dati astratto (a strati ) è fatta a cipolla.

modelli di struttura di un sistema
- repository 
- client server
- macchina a strati ( livelli di cipolla )

modello **call-return**: gestisce il controllo; in profondità, e NON a strato is also centralizzato. 

modello **Manager**: a "centralina" gestisce il controllo a modo centralization

## modelli di controllo basato su eventi 

modello **Broadcast**: "the listener", politiche di controllo, sollevando un eccezione, un evento, etc (message handler) 

Modello **Broadcasting selettivo**: 

modello **interrupt-driven**: 

tutto quanto vuol dire di pensare alle cosa a livello astratto di schema, e NON a livello implementativo, non ci frega nulla del linguaggio a sto punto di programmazione!!. 

modello riferimento OSI, sono dei standard e non oggetti che si interfacciano con la realtà

l'applicazione è buona quando l'accoppiamento è lasco, quando si modifica una componente, bisogna aver il minimo rischio di ricaduta sul resto del codice 

accoppiamento stretto, accoppiamento lasco.

servente di moduli e clienti di altri sottosistemi 

avere profonde gerarchie di ereditarietà fa pugni con la coesione e l'accoppiamento.
bisogna fare attenzione alle profondità 






### Tags









 
