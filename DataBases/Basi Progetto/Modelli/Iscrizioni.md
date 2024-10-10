
# Classe `Iscrizioni`

```python
from project import db
from sqlalchemy import ForeignKey

class Iscrizioni(db.Model):
    __tablename__ = 'iscrizioni'
    id_iscrizione = db.Column(db.Integer, primary_key = True)
    data_iscrizione = db.Column(db.Date)
    studente_id = db.Column(db.String(6), ForeignKey('studenti.matricola'))
    appello_id = db.Column(db.Integer, ForeignKey('appelli.id_appello'))
    
    def __init__(self, data_iscrizione, studente_id, appello_id):
        self.data_iscrizione = data_iscrizione
        self.studente_id = studente_id
        self.appello_id = appello_id
```


## Dipendenze
Il codice fa uso delle seguenti dipendenze:
- `db` dal modulo `project`
- `ForeignKey` dal modulo `sqlalchemy`

###Membri della classe

La classe `Iscrizioni` ha i seguenti membri:

- `id_iscrizione`: Colonna di tipo `db.Integer` che rappresenta l'ID dell'iscrizione e viene utilizzato come chiave primaria.
- `data_iscrizione`: Colonna di tipo `db.Date` che rappresenta la data di iscrizione.
- `studente_id`: Colonna di tipo `db.String(6)` che rappresenta la matricola dello studente che ha effettuato l'iscrizione. Questa colonna fa riferimento alla tabella "studenti" tramite la chiave esterna (`ForeignKey('studenti.matricola')`).
- `appello_id`: Colonna di tipo `db.Integer` che rappresenta l'ID dell'appello a cui lo studente si è iscritto. Questa colonna fa riferimento alla tabella "appelli" tramite la chiave esterna (`ForeignKey('appelli.id_appello')`).