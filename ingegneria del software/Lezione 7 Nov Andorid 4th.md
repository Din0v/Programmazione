# misc notes 

1. programmazione asincrona in android (il mondo dentro il mondo)
2. background task ( e le sue sotto voci )
3. task ( app running in background ) 
4. il download svuota il buffer della scheda di rete 
5. sempre importante le politiche di scheduling
6. la presa della bastillia 
7. coroutines ( sta parlando di un aggeggio che esiste in kotlin e non in java Attenzione !!)
8. modi di dire che si accavallano 
9. java threads aren't the similar to the ones of android !! read the (asynchronous work with java threads)
10. nomenclatura
11. Excutor: le entità che eseguno le task in backgroud loro astraggono a livello di pattern chi sta esegunado le cose che volete eseguire 
12. scheduling cooperativo (metto nelle mani del programmatore di fare context switch yield(metodo statico senza argomenti)) vs  preemptive scheduler ((esegue per un quanto di tempo il tuo thread, ed ogni tanto di viene tolta, dal timer, round-robin ))
13. l'excutor è il modo di eseguire; dal punto di vista del scheduler 
14. gli excutor si sforzano a spawnare il thread chiedere al kernel di darmi un thread esistente, anziche crearne uno e dispendere il tempo di creazione e distruzione 
15. le pool servono esattamente a questo specialmente nei program super concorrenti! 
16. il pattern non è un IF, o un try catch dato che stiamo programmando in maniera asincrona 
17. thread diversi non condividono lo stack!!
18. serve un modo per comunicare l'errore a chi mi ha spawnato 
19. java thread (documentation) the example code is a design pattern ci mostra come programmare 
20. MVC programming pattern 
21. MDA model "dreaming" architecture ?
22. Handlers: are the entities ( la mia app vuole fare un qualcosa di asincrono ma non subito ) lo mette in fine alla coda "0.4 ms" they are followed by the mega spooler of android 
23. un handler non è un task in background che lo fa il spooler di android. 
24. handlers are fake constructors 
25. vsync oh oh ho appena finito di designare il frame (aspetta il segnale dallo schermo che indica al software che ha finito di disegnare)
26. double buffer in graphics 
27. è un po' una bolgia sono delle usanze ( for confusing naming )
28. post serve a dire Ehi android appena hai tempo eseguimi il runnable 
29. imparare a usare i handler !!
30. i handler devono essere brevi e POCO importanti per non bloccare il main loop 
31. i punti di rendez-vous "joiner"
32. 
33. 
34.  