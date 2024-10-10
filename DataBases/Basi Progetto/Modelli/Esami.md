## Classe `Esami`

```python
from project import db
from sqlalchemy import ForeignKey
from project.models.docenti import Docenti
from sqlalchemy.orm import relationship


class Esami(db.Model):
    
    __tablename__ = 'esami'
    id_esame = db.Column(db.Integer, primary_key = True)
    nome_esame = db.Column(db.String(50), nullable=False)
    num_prove = db.Column(db.Integer, nullable=False)  
    docente_id = db.Column(db.Integer, ForeignKey('docenti.id_docente'))
    
    proveE = relationship("Prove", backref="esami")
    esami_superatiE = relationship("Esami_superati", backref="esami")
    
    def __init__(self, nome_esame, num_prove, docente_id):
        self.nome_esame = nome_esame
        self.num_prove = num_prove
        self.docente_id = docente_id
        
        
```

## Dipendenze
Il codice fa uso delle seguenti dipendenze:

- `db` dal modulo `project`
- `ForeignKey` dal modulo `sqlalchemy`
- `Docenti` dal modulo `project.models.docenti`
- `relationship` dal modulo `sqlalchemy.orm`

Assicurarsi che queste dipendenze siano presenti e correttamente installate per eseguire il codice.

## La classe `Esami` ha i seguenti membri:

- `id_esame`: Colonna di tipo `db.Integer` che rappresenta l'ID dell'esame e viene utilizzato come chiave primaria.
- `nome_esame`: Colonna di tipo `db.String(50)` che rappresenta il nome dell'esame. Questa colonna non può essere vuota (`nullable=False`).
- `num_prove`: Colonna di tipo `db.Integer` che rappresenta il numero di prove associate all'esame. Questa colonna non può essere vuota (`nullable=False`).
- `docente_id`: Colonna di tipo `db.Integer` che rappresenta l'ID del docente associato all'esame. Questa colonna fa riferimento alla tabella "docenti" tramite la chiave esterna (`ForeignKey('docenti.id_docente')`).