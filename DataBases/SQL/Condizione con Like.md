# Condizioni in SQL 

Query the list of _CITY_ names ending with vowels (a, e, i, o, u) from **STATION**. Your result _cannot_ contain duplicates.

![[Pasted image 20240202074918.png]]

```SQL 
SELECT DISTINCT City 
FROM STATION 
WHERE RIGHT(City, 1) IN ('a', 'e', 'i', 'o', 'u');
```

attenzione alla keyword ==DISTINCT== restituisce solo le condizioni i risultati distinti 

==RIGHT== prende le lettere da destra  a sinistra dalla colonna valuta "City" e piglia solo una lettera. 


### Tags 
#Databases 
#SQL 