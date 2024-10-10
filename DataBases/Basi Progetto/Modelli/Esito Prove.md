# Classe `Esito_prove`

```python 
from datetime import datetime
from project import db
from sqlalchemy import ForeignKey


class Esito_prove(db.Model):
    __tablename__ = 'esito_prove'
    id_superamento = db.Column(db.Integer, primary_key = True)
    voto = db.Column(db.Integer)
    validita = db.Column(db.Boolean)
    data_scadenza = db.Column(db.Date)
    prova_id = db.Column(db.Integer, ForeignKey('prove.id_prova'))
    studente_id = db.Column(db.String(6), ForeignKey('studenti.matricola'))
    
    def __init__(self, voto, validita, data_scadenza, prova_id, studente_id):
        self.voto = voto
        self.validita = validita
        self.data_scadenza = data_scadenza
        self.prova_id = prova_id
        self.studente_id = studente_id
    
```
## Dipendenze

Il codice utilizza le seguenti dipendenze:

- `datetime` dal modulo `datetime`
- `db` dal modulo `project`
- `ForeignKey` dal modulo `sqlalchemy`

## Membri della classe

La classe `Esito_prove` ha i seguenti membri:

- `id_superamento`: Colonna di tipo `db.Integer` che rappresenta l'ID di superamento delle prove e viene utilizzato come chiave primaria.
- `voto`: Colonna di tipo `db.Integer` che rappresenta il voto ottenuto nelle prove.
- `validita`: Colonna di tipo `db.Boolean` che indica se l'esito delle prove è valido o no.
- `data_scadenza`: Colonna di tipo `db.Date` che rappresenta la data di scadenza delle prove.
- `prova_id`: Colonna di tipo `db.Integer` che rappresenta l'ID della prova associata all'esito.
- `studente_id`: Colonna di tipo `db.String(6)` che rappresenta la matricola dello studente associato all'esito.

---

## Funzione `aggiorna_valore()`

```python 
def aggiorna_valore():
    data_letta = datetime.now().date()  # Ottieni la data corrente
    records = db.session.query(Esito_prove).filter(Esito_prove.data_scadenza < data_letta)

    for record in records:
        record.validita = False
```


## Descrizione

La funzione `aggiorna_valore()` è progettata per aggiornare l'attributo `validita` degli oggetti `Esito_prove` in base alla data corrente. Questa funzione utilizza una connessione al database per eseguire una query e ottenere i record che soddisfano determinati criteri di filtro.

## Funzionamento

1. Ottieni la data corrente: La funzione inizia ottenendo la data corrente utilizzando `datetime.now().date()` e la memorizza nella variabile `data_letta`. Questo valore verrà utilizzato come punto di riferimento per confrontare la data di scadenza degli oggetti `Esito_prove`.

2. Esegui la query nel database: La funzione utilizza `db.session.query(Esito_prove)` per avviare una query sulla tabella `Esito_prove` nel database. Questa query restituisce un oggetto che rappresenta il risultato della query.

3. Applica un filtro alla query: Viene applicato un filtro alla query utilizzando il metodo `filter()` per selezionare solo i record in cui la data di scadenza (`Esito_prove.data_scadenza`) è inferiore alla data corrente (`data_letta`). Questo assicura che solo i record con una data di scadenza precedente vengano considerati per l'aggiornamento.

4. Itera sui record: Viene avviato un ciclo `for` per iterare su ciascun record ottenuto dalla query. Ogni record viene assegnato alla variabile `record` durante ciascuna iterazione.

5. Aggiorna l'attributo `validita`: All'interno del ciclo `for`, l'attributo `validita` dell'oggetto `record` viene impostato su `False`. Ciò indica che l'esito delle prove non è più valido.

6. Salvataggio dei cambiamenti: Dopo aver completato l'iterazione su tutti i record, è necessario eseguire il commit delle modifiche al database utilizzando `db.session.commit()`. Questo salva effettivamente i cambiamenti apportati all'attributo `validita` degli oggetti `Esito_prove`.