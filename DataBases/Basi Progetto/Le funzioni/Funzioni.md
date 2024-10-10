```Python
from project import db
from sqlalchemy import text
from flask import render_template
from project.models.esito_prove import Esito_prove
from sqlalchemy.exc import DatabaseError

def trova_indici_ripetizione(lista_di_tuple):
    occorrenze = {}
    indici_ripetuti = []

    for indice, tupla in enumerate(lista_di_tuple):
        chiave = tupla[:-1]  # Escludi l'ultimo valore dalla chiave

        if chiave in occorrenze:
            occorrenze[chiave].append(indice)
        else:
            occorrenze[chiave] = [indice]

    for lista_indici in occorrenze.values():
        if len(lista_indici) > 1:
            indici_ripetuti.append(lista_di_tuple[lista_indici[0]][-1])  # Aggiungi il quarto valore all'output
    return indici_ripetuti

```

La funzione `trova_indici_ripetizione(lista_di_tuple)` è un'implementazione di una logica per trovare gli indici delle ripetizioni in una lista di tuple. Di seguito è descritto il modo di funzionamento di questa funzione:

1. Viene inizializzato un dizionario chiamato `occorrenze` per tenere traccia delle occorrenze di ciascuna chiave.
2. Viene inizializzata una lista chiamata `indici_ripetuti` per memorizzare gli indici delle ripetizioni.
3. Viene eseguito un ciclo `for` utilizzando la funzione `enumerate()` per iterare sugli elementi della lista di tuple insieme ai relativi indici.
4. Viene estratta la chiave da ogni tupla escludendo l'ultimo valore.
5. Se la chiave è già presente nel dizionario `occorrenze`, viene aggiunto l'indice corrente alla lista degli indici corrispondenti. Altrimenti, viene creato un nuovo elemento nel dizionario con la chiave e l'indice corrente come unico elemento della lista.
6. Viene eseguito un secondo ciclo `for` sui valori del dizionario `occorrenze`. Se la lista degli indici ha una lunghezza maggiore di 1, significa che ci sono ripetizioni per quella chiave e l'indice della prima occorrenza viene aggiunto alla lista `indici_ripetuti`.
7. Alla fine del ciclo, viene restituita la lista `indici_ripetuti` contenente gli indici delle ripetizioni.

---

## Funzione Elimina prove ripetute
```Python
def elimina_prove_ripetute():
    try:
        query = text("""
        SELECT e.id_esame, s.matricola, p.tipo_prova, ep.id_superamento
        FROM studenti s
        JOIN esito_prove ep ON s.matricola = ep.studente_id
        JOIN prove p ON p.id_prova = ep.prova_id
        JOIN esami e ON e.id_esame = p.esame_id
        GROUP BY s.matricola, p.tipo_prova, e.id_esame, ep.id_superamento
        ORDER BY s.matricola, e.id_esame, p.tipo_prova
        """)
    
  
        results = db.session.execute(query)
    
        lista_di_tuple = [tuple(row) for row in results] 
    
        indici_ripetuti = trova_indici_ripetizione(lista_di_tuple)

        for indice in indici_ripetuti:
            db.session.query(Esito_prove).filter(Esito_prove.id_superamento.in_([indice])).update({"validita": False})
            db.session.commit()
    except DatabaseError as e:
        db.session.rollback()  # Annulla le modifiche al database
        error_msg = str(e)  # Ottieni il messaggio di errore
        return render_template('error.html', error=error_msg)
        
def str_to_bool(s):
    if s == 'False':
        res = False
    else:
        res = True 
    return res

```

La funzione `elimina_prove_ripetute()` gestisce l'eliminazione delle prove ripetute nel database. Di seguito è descritto il modo di funzionamento di questa funzione:

1. Viene eseguita una query sul database utilizzando il metodo `execute()` della sessione del database. La query seleziona diverse colonne da diverse tabelle e le raggruppa per matricola studente, tipo di prova, ID esame e ID di superamento. I risultati vengono ordinati per matricola studente, ID esame e tipo di prova.
2. I risultati della query vengono memorizzati nella variabile `results`.
3. Viene creato un elenco di tuple chiamato `lista_di_tuple`, in cui ogni riga di risultati della query viene convertita in una tupla.
4. Viene chiamata la funzione `trova_indici_ripetizione(lista_di_tuple)` passando la lista di tuple come parametro. Questa funzione restituisce una lista di indici che corrispondono alle ripetizioni trovate.
5. Viene eseguito un ciclo `for` su `indici_ripetuti`. Per ciascun indice ripetuto, viene eseguita una query di aggiornamento sul database per impostare il valore `validita` a `False` per l'entità `Esito_prove` corrispondente all'indice.
6. Le modifiche al database vengono confermate utilizzando `db.session.commit()`.

--- 
## Funzione Trova matricola 
```Python 
def trova_matricola(query, matricola):
    trovato = False
    results = db.session.execute(query)
    for matr in results:
        if matr.matricola==matricola:
            trovato = True
    return trovato
```

La funzione `str_to_bool(s)` converte una stringa in un valore booleano. Restituisce `False` se la stringa è uguale a `'False'`, altrimenti restituisce `True`.

La funzione `trova_matricola(query, matricola)` esegue una query sul database utilizzando il parametro `query` specificato e controlla se la matricola specificata è presente nei risultati. Restituisce `True` se la matricola viene trovata, altrimenti restituisce `False`.

### Tags
#progetto_Basi
