# Storico Prove:

```python
from project import app
from flask import render_template
from project import db
from project.models.esami import Esami
from project.models.studenti import Studenti
from project.models.esito_prove import Esito_prove, aggiorna_valore
from project.models.prove import Prove
from project.models.appelli import Appelli
from sqlalchemy.exc import DatabaseError
import project.views.funzioni as funzioni


@app.route('/storico_prove')
def storico_prove():
    aggiorna_valore()
    funzioni.elimina_prove_ripetute()
    try:
        res = db.session.query(Studenti.matricola, Studenti.cognome_studente, Studenti.nome_studente, Esami.nome_esame,
                           Esito_prove.voto, Appelli.data_appello, Esito_prove.data_scadenza, Prove.tipo_prova,Esito_prove.validita)\
        .join(Esito_prove, Studenti.matricola==Esito_prove.studente_id)\
        .join(Prove, Prove.id_prova==Esito_prove.prova_id)\
        .join(Esami, Esami.id_esame==Prove.esame_id)\
        .join(Appelli, Appelli.prova_id == Prove.id_prova)\
        .order_by(Studenti.matricola)\
        .all()
        return render_template('storico_prove.html', results=res)
    except DatabaseError as e:
        db.session.rollback()  # Annulla le modifiche al database
        error_msg = str(e)  # Ottieni il messaggio di errore
        return render_template('error.html', error=error_msg)
```
	
La funzione `storico_prove()` gestisce l'endpoint `/storico_prove` e definisce il comportamento associato a tale endpoint. Di seguito è descritto il modo di funzionamento di questa funzione:

1. Viene chiamata la funzione `aggiorna_valore()` per eseguire un aggiornamento del valore associato agli esiti delle prove. Questo potrebbe includere il controllo delle scadenze delle prove e l'aggiornamento della validità degli esiti in base ai criteri definiti.

2. Viene chiamata la funzione `elimina_prove_ripetute()` per eliminare eventuali prove ripetute. Questa funzione potrebbe impostare a `False` la validità degli esiti di prove che sono state ripetute in seguito.

3. All'interno di un blocco `try`, viene eseguita una query sul database utilizzando il metodo `query()` della sessione del database. La query recupera diverse informazioni relative agli studenti, agli esami, agli esiti delle prove, alle prove stesse e agli appelli. Viene utilizzato il metodo `join()` per collegare le tabelle corrispondenti in base alle relazioni definite nei modelli. Inoltre, i risultati della query vengono ordinati per matricola degli studenti utilizzando il metodo `order_by()`.

4. I risultati della query vengono memorizzati nella variabile `res`.

5. Viene restituito un template HTML chiamato `'storico_prove.html'`, passando i risultati ottenuti come parametro `results`.

6. Nel caso si verifichi un errore di database di tipo `DatabaseError`, viene eseguito un blocco `except` per gestire l'eccezione. Le modifiche al database vengono annullate utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`.

7. Viene restituito un template HTML chiamato `'error.html'`, passando il messaggio di errore come parametro `error`.