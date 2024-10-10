# Funzione Prossimi Appelli

```python
from project import app
from flask import render_template, request, redirect
from project import db
from sqlalchemy import text
from project.models.iscrizioni import Iscrizioni
from datetime import datetime
from sqlalchemy.exc import DatabaseError
import project.views.funzioni as funzioni
```

Il codice inizia importando le librerie e i moduli necessari per il funzionamento dell'applicazione. Di seguito è una breve descrizione dei moduli importati:

- `app`: rappresenta l'istanza dell'applicazione Flask. ( che è il programma da eseguire che si trova nella cartella project)
  
- `render_template`: viene utilizzato per generare il rendering di template HTML tramita il framework di jinja 2.
  
- `request`: permette di accedere ai dati inviati dal client HTTP.
  
- `redirect`: viene utilizzato per reindirizzare l'utente a una diversa pagina URL.
  
- `db`: rappresenta l'oggetto del database SQLAlchemy.
  
- [`text`](https://www.adamsmith.haus/python/docs/sqlalchemy.sql.expression.text): viene utilizzato per creare query SQL. 
  
- `Iscrizioni`: è il modello di dati per le iscrizioni.
  
- `datetime`: viene utilizzato per ottenere la data e l'ora correnti.
  
- `DatabaseError`: rappresenta un'eccezione per gli errori del database.
  
- `project.views.funzioni`: è un modulo personalizzato che contiene le nostre funzioni ausiliari.

---- 
## La Funzione Prossimi_Appelli

```python
@app.route('/prossimi_appelli')
def prossimi_appelli():
    try:
        today = datetime.now().date()
        query = text("""SELECT e.nome_esame, a.data_appello, a.ora, a.aula, a.note, 
                 COUNT(i.id_iscrizione) AS num_iscritti, a.id_appello
            FROM appelli a
            LEFT JOIN iscrizioni i ON a.id_appello = i.appello_id
            LEFT JOIN prove p ON p.id_prova = a.prova_id
            LEFT JOIN esami e ON e.id_esame = p.esame_id
            WHERE a.data_appello >= :today
            GROUP BY e.nome_esame, a.data_appello, a.ora, a.aula, a.note, a.id_appello
            ORDER BY a.data_appello ASC
            """)
        result = db.session.execute(query,{"today": today})
        # Salva i risultati in una lista
        results = []
        for row in result:
            results.append(row)
        # Restituisci il template HTML con i risultati
        return render_template('prossimi_appelli.html', results=results)
    except DatabaseError as e:
        db.session.rollback()  # Annulla le modifiche al database
        error_msg = str(e)  # Ottieni il messaggio di errore
        return render_template('error.html', error=error_msg)

```
## Parametri

La funzione `prossimi_appelli()` non accetta alcun parametro.

## Funzionamento

La funzione viene associata al URL `\prossimi appelli`

1. La variabile `today` viene inizializzata con la data odierna utilizzando `datetime.now().date()`. Questa informazione sarà utilizzata nella query per filtrare gli appelli futuri.
    
2. Viene costruita una query SQL utilizzando la classe `text` del modulo `sqlalchemy`. La query seleziona i seguenti campi dalla tabella degli appelli (`appelli`) e si unisce ad altre tabelle (`iscrizioni`, `prove`, `esami`) per ottenere informazioni aggiuntive sugli appelli e sulle iscrizioni:
    
    - `e.nome_esame`: nome dell'esame.
    - `a.data_appello`: data dell'appello.
    - `a.ora`: ora dell'appello.
    - `a.aula`: aula in cui si svolge l'appello.
    - `a.note`: note sull'appello.
    - `COUNT(i.id_iscrizione) AS num_iscritti`: numero di iscritti per ogni appello.
    - `a.id_appello`: ID dell'appello.
    
    La clausola `WHERE` viene utilizzata per selezionare solo gli appelli con data maggiore o uguale alla data odierna.
    
    La clausola `GROUP BY` viene utilizzata per raggruppare gli appelli per esame, data, ora, aula, note e ID appello.
    
    La clausola `ORDER BY` viene utilizzata per ordinare gli appelli in base alla data in ordine ascendente.
    
3. La query viene eseguita utilizzando `db.session.execute()` e passando la query SQL e i parametri `{"today": today}`.
    
4. I risultati della query vengono salvati in una lista chiamata `results` utilizzando un ciclo `for`.
    
5. Viene restituito un template HTML chiamato `'prossimi_appelli.html'` passando i risultati come parametro `results`.
    
6. Se si verifica un errore del database di tipo `DatabaseError`, vengono annullate le modifiche al database utilizzando `db.session.rollback()` e viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore.
    

## Restituzione dei valori

La funzione restituisce il risultato della chiamata alla funzione `render_template()`, che genera un template HTML con i risultati degli appelli.

### Gestione degli errori

Nel caso in cui si verifichi un errore del database di tipo `DatabaseError`, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)` e viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

## Note aggiuntive

Assicurati di aver importato correttamente i moduli necessari come `datetime`, `text` da `sqlalchemy`, `DatabaseError` da `sqlalchemy.exc`, `render_template` da `flask` e `db` da `project`. Verifica anche che la configurazione del database sia corretta per consentire l'esecuzione delle query.

---
# La funzione Nuova iscrizione 
```Python
@app.route('/nuova_iscrizione', methods=['POST'])
def nuova_iscrizione(): 
    try:
        studente = request.form['studente_id']
        appello = int(request.form['appello_id'])
        today = datetime.now().date()
        if 'iscriviti' in request.form:
            query = text("""SELECT matricola FROM studenti """)
            if funzioni.trova_matricola(query, studente):
                new_iscrizione = Iscrizioni(today, studente, appello)
                db.session.add(new_iscrizione)
                db.session.commit()
            else:
                return render_template('/matricola_non_trovata.html')
        elif 'cancellati' in request.form:
            query = text(""" SELECT studente_id AS matricola FROM iscrizioni """)
            if funzioni.trova_matricola(query, studente):
                query = text("""DELETE FROM iscrizioni WHERE studente_id = :studente AND appello_id = :appello""")
                db.session.execute(query.params(studente=studente, appello=appello))
                db.session.commit()
            else:
                return render_template('/matricola_non_trovata.html')
        return redirect('/prossimi_appelli')
    
    except DatabaseError as e:
        db.session.rollback()  # Annulla le modifiche al database
        error_msg = str(e)  # Ottieni il messaggio di errore
        return render_template('error.html', error=error_msg)

```

## Parametri

La funzione `nuova_iscrizione()` non accetta alcun parametro.

## Funzionamento

1. La funzione viene associata all'URL `/nuova_iscrizione` tramite l'annotazione `@app.route('/nuova_iscrizione', methods=['POST'])`.
 
2. La funzione riceve una richiesta **POST** e ottiene i valori dei campi `studente_id` e `appello_id` dal form inviato utilizzando `request.form['studente_id']` e `request.form['appello_id']`, rispettivamente.

3. Viene ottenuta la data odierna utilizzando `datetime.now().date()` e assegnata alla variabile `today`.

4. Se il valore `'iscriviti'` è presente nel form inviato, viene eseguito il seguente blocco di codice:
    
    - Viene definita una **query SQL** utilizzando la classe `text` del modulo `sqlalchemy` per selezionare la colonna `matricola` dalla tabella degli studenti (`studenti`).
    - Viene chiamata la funzione `funzioni.trova_matricola(query, studente)` per verificare se la matricola dello studente è presente nella tabella degli studenti utilizzando la query definita. Se la matricola esiste, viene eseguito il seguente blocco di codice:
        - Viene creata una nuova istanza della classe `Iscrizioni` passando la data odierna, la matricola dello studente e l'ID dell'appello.
        - La nuova iscrizione viene aggiunta alla sessione del database utilizzando `db.session.add(new_iscrizione)`.
        - Le modifiche vengono confermate e salvate nel database utilizzando `db.session.commit()`.
    - Se la matricola dello studente non è stata trovata nella tabella degli studenti, viene restituito un template HTML chiamato `'matricola_non_trovata.html'` utilizzando `render_template()`.

5. Se il valore `'cancellati'` è presente nel form inviato, viene eseguito il seguente blocco di codice:
 
    - Viene definita una query SQL utilizzando la classe `text` del modulo `sqlalchemy` per selezionare la colonna `studente_id` come `matricola` dalla tabella delle iscrizioni (`iscrizioni`).
    - Viene chiamata la funzione `funzioni.trova_matricola(query, studente)` per verificare se la matricola dello studente è presente nella tabella delle iscrizioni utilizzando la query definita. Se la matricola esiste, viene eseguito il seguente blocco di codice:
     - Viene definita una nuova query SQL utilizzando la classe `text` per eliminare l'iscrizione dello studente specificato e l'appello specificato dalla tabella delle iscrizioni.
    - La query viene eseguita utilizzando `db.session.execute(query.params(studente=studente, appello=appello))`.
    - Le modifiche vengono confermate e salvate nel database utilizzando `db.session.commit()`.
    - Se la matricola dello studente non è stata trovata nella tabella delle iscrizioni, viene restituito un template HTML chiamato `'matricola_non_trovata.html'` utilizzando `render_template()`.
 
6. Dopo aver eseguito l'azione richiesta con successo (iscrizione o cancellazione), l'utente viene reindirizzato alla pagina degli appelli utilizzando `redirect('/prossimi_appelli')`.

7. Se si verifica un errore del database di tipo `DatabaseError`, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)` e viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.


## Restituzione dei valori

La funzione restituisce il risultato della chiamata alla funzione `redirect('/prossimi_appelli')` dopo aver eseguito con successo l'iscrizione o la cancellazione. In caso di errore, viene restituito un template HTML di errore con il messaggio di errore appropriato.

## Gestione degli errori

Nel caso in cui si verifichi un errore del database di tipo `DatabaseError`, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. 
Viene estratto il messaggio di errore come stringa utilizzando `str(e)` e viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.