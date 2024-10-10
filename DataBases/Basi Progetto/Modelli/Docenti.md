## Docenti

```python 
from project import db
from sqlalchemy.orm import relationship

class Docenti(db.Model):
    __tablename__ = 'docenti'
    id_docente = db.Column(db.Integer, primary_key = True)
    nome_docente = db.Column(db.String(20), nullable=False)
    cognome_docente = db.Column(db.String(20), nullable=False)
    email_docente = db.Column(db.String(40), nullable=False)
    dipartimento = db.Column(db.String(30), nullable=False)
    password = db.Column(db.String(30), nullable=False)
    
    esamiD = relationship("Esami", backref="docenti")
    
    #costruttore
    def __init__(self, nome_docente, cognome_docente, email_docente, dipartimento, password):
        self.nome_docente = nome_docente
        self.cognome_docente = cognome_docente
        self.email_docenet = email_docente
        self.dipartimento = dipartimento
        self.password = password
        
    
    
```

## Attributi della classe:

- `id_docente:` Un intero che rappresenta l'identificatore univoco del docente (primary key).
- `nome_docente:` Una stringa di massimo 20 caratteri che rappresenta il nome del docente. Questo attributo non può essere vuoto (nullable=False).
- `cognome_docente:` Una stringa di massimo 20 caratteri che rappresenta il cognome del docente. Anche questo attributo non può essere vuoto (nullable=False).
- `email_docente:` Una stringa di massimo 40 caratteri che rappresenta l'email del docente. Anche questo attributo non può essere vuoto (nullable=False).
- `dipartimento:` Una stringa di massimo 30 caratteri che rappresenta il dipartimento di appartenenza del docente. Anche questo attributo non può essere vuoto (nullable=False).
- `password:` Una stringa di massimo 30 caratteri che rappresenta la password del docente. Anche questo attributo non può essere vuoto (nullable=False).

