# lezione android studio Prof Alvise

1. ```ActivityMainBinding;```serve ad avere un oggetto,  fornisce un dicitionary (una struttura dati associativa) per i XML.
2. XML e java sono due realtà parallele.
3. nel elenco del binding ci sono robe che non sono nostre!! roba che non ho definito io
4. sono in **bold** perché sono pubblici !! attenzioni ai tipi e ai metodi!
5. ```@android:drawable```, indirizza la grafica del SDK di default.
6. **code behind**; what is it ? il codice che sta dietro la grafica cliccata!
7. nel XML non c'è il divenire nel tempo! è una istantanea
8. l'importanza delle lambda nei ```onClickListener``` è un lungo argomento che ha il tipo di lambda
```java
binding.mybutton.setOnClickListener((view)-> binding .mybutton.setText("cambiato"))  //cambia stringa del bottone stesso
```
9. la mia lambda è parametrica, dipende di chi ha scatenato l'evento.
10. siamo in un modo dove il subtyping è valido 
11. la risoluzione del overloading VIENE DOPO di aver diZuccherato!!!
12. eta espansione (nelle lambda)
13. desugaring of the lambda in java
14. c'è un modo per permettere al sistema operativo il dispatcher che è un pezzo di kernel che limita i tempi dei callback 
15. un altro thread per controllare un altra operazione che non "risponde" aka watchdog 
16. non tutti i thread non possono renderizzare 
17. solo il main thread possono chiamare un thread che ha un effetto sul render 
18. è un sistema di spooling 
19. 