# Appelli
```python
from project import db
from sqlalchemy.orm import relationship
from sqlalchemy import ForeignKey
from sqlalchemy.orm import relationship

class Appelli(db.Model): # classe Appelli sottoclasse di db.Model
    __tablename__ = 'appelli'
    id_appello = db.Column(db.Integer, primary_key = True) 
    data_appello = db.Column(db.Date)
    ora = db.Column(db.String(10))
    aula = db.Column(db.String(20))
    note = db.Column(db.String(255))
    prova_id = db.Column(db.Integer, ForeignKey('prove.id_prova'))
    
    iscrizioniA = relationship("Iscrizioni", backref="appelli")
    
    def __init__(self, data_appello, ora, aula, note, prova_id): #costruttore di un oggetto della classe Appelli
        self.data_appello = data_appello
        self.ora = ora
        self.aula = aula
        self.note = note
        self.prova_id = prova_id

        
```

La classe `Appelli` è definita nel codice fornito e rappresenta una tabella del database chiamata "appelli". Questa classe è una sottoclasse di `db.Model`, che indica che viene utilizzata come modello per una tabella del database all'interno di un'applicazione Flask.

Attributi della classe `Appelli`:

- `id_appello`: Un attributo di tipo `db.Column` che rappresenta la chiave primaria della tabella "appelli". È di tipo intero (`db.Integer`) e viene specificato come colonna primaria (`primary_key=True`).
- `data_appello`: Un attributo di tipo `db.Column` che rappresenta la data dell'appello. È di tipo `db.Date`, che indica una data senza orario.
- `ora`: Un attributo di tipo `db.Column` che rappresenta l'ora dell'appello. È di tipo `db.String(10)`, che consente di memorizzare una stringa di lunghezza massima di 10 caratteri.
- `aula`: Un attributo di tipo `db.Column` che rappresenta l'aula in cui si svolge l'appello. È di tipo `db.String(20)`, che consente di memorizzare una stringa di lunghezza massima di 20 caratteri.
- `note`: Un attributo di tipo `db.Column` che rappresenta eventuali note aggiuntive sull'appello. È di tipo `db.String(255)`, che consente di memorizzare una stringa di lunghezza massima di 255 caratteri.
- `prova_id`: Un attributo di tipo `db.Column` che rappresenta l'ID della prova associata all'appello. È di tipo `db.Integer` e specifica una relazione di chiave esterna (`ForeignKey('prove.id_prova')`) con la tabella "prove".

