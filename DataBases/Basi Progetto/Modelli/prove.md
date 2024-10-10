
```python 
from project import db
from sqlalchemy import ForeignKey
from sqlalchemy.orm import relationship

class Prove(db.Model):
    __tablename__ = 'prove'
    id_prova = db.Column(db.Integer, primary_key = True)
    tipo_prova = db.Column(db.String(20))
    esame_id = db.Column(db.Integer, ForeignKey('esami.id_esame'))
    
    esito_proveP = relationship("Esito_prove", backref="prove")
    appelliP = relationship("Appelli", backref="prove")
    
    def __init__(self, tipo_prova, esame_id):
        self.tipo_prova = tipo_prova
        self.esame_id = esame_id
```f