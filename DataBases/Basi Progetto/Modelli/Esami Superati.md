# Esami Superati
```python 
from project import db
from sqlalchemy import ForeignKey
from project.models.studenti import Studenti
from project.models.esami import Esami


class Esami_superati(db.Model):
    
    __tablename__ = 'esami_superati'
    voto = db.Column(db.Integer)
    lode = db.Column(db.Boolean)
    data_registrazione = db.Column(db.Date)
    studente_id = db.Column(db.String, ForeignKey('studenti.matricola'), primary_key=True)
    esame_id = db.Column(db.Integer, ForeignKey('esami.id_esame'), primary_key=True)
    
    
    def __init__(self, voto, lode, data_registrazione, studente_id, esame_id):
        self.voto = voto
        self.lode = lode
        self.data_registrazione = data_registrazione
        self.studente_id = studente_id
        self.esame_id = esame_id
```


## Dipendenze

Il codice fa uso delle seguenti dipendenze:

- `db` dal modulo `project`
- `ForeignKey` dal modulo `sqlalchemy`
- `Studenti` dal modulo `project.models.studenti`
- `Esami` dal modulo `project.models.esami`

## Classe `Esami_superati`

## Membri della classe

La classe `Esami_superati` ha i seguenti membri:

- `voto`: Colonna di tipo `db.Integer` che rappresenta il voto ottenuto nell'esame superato.
- `lode`: Colonna di tipo `db.Boolean` che indica se l'esame superato è stato preso con lode o no.
- `data_registrazione`: Colonna di tipo `db.Date` che rappresenta la data di registrazione dell'esame superato.
- `studente_id`: Colonna di tipo `db.String` che rappresenta la matricola dello studente che ha superato l'esame. È anche utilizzata come chiave primaria insieme all'attributo `esame_id`.
- `esame_id`: Colonna di tipo `db.Integer` che rappresenta l'ID dell'esame superato. È anche utilizzata come chiave primaria insieme all'attributo `studente_id`.