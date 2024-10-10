# Android studio tutorial 
1. emula tutto l'android OS, (Io l'ho provato con il mio cellulare after android debugging)
2. Tags, nested tags, Include tag
3. XML file have the reverse convention as it's parrent class
	> activity_main.xml
	> MainActivity.java
4. why? per rispettare l'ordine alfabetico (doesn't mess up the order since they are ordered alphabetically)
5. a cosa serve dare un noma ad un (layout/entità) ?
6. > è una questione di binding, e per questo e che le devo dare un nome!! "battezzandolo con un nome"
7. ```Match_parent``` è una keyword che setta la schermata dell app / activity 
8. 100dp è equivalente a ```Match_parent```
>[!note]
>cercare le unità di misura nella documentazione
9. appbar vs toolbar, l'app bar contiene la tool bar ( for theming), alcune app non hanno la app bar sono sempre in fullscreen I.E videogiochi 
10. Floating: is a button that stays there no matter the change of activity _floating action button_
11. ```Bottom|end``` bot to the right
12. ```top|start``` top to the left. 
13. the analogy looks like a typing document / terminal
14. il detachment della informazione, staccare e astrarre. 
15. file XML di strings, permette le app multilingua (La localizzazione)
16. ```CoordinatorLayout``` documentation. sono dei tag speciali, 
17. does the coordinator layout gestisce lo scaling ? 
18. fragment == stato grafico del activity 
19. un frammento può cambiare il che è una sotto-regione  che si possono cambiare senza dover rerendirizzare il tutto.
20. i fragment sono cosi potenti che possono fare girare tutta un'app :p 
## ciclo di vita di un activity: 
1. un activity è associata ad una classe java che fa "maggiordomo" di casa (menu, listener, button press..)
2. android volevano un linguaggio, che non riesce a definire un costruttore! 
3. non poi definire un costruttore in android quando si definisce una activity. 
4. congelare lo stato senza disperdere energia.
5. Documentation ```the activity life cycle```
6. 