# Data definition language 

DDL è un insieme di comandi SQL utilizzati per modificare la struttura dei database, comprende operazioni per creare, alterare ed eliminare, schede, indici, tabelle e altri oggetti di database. 

vedi [[DML]]

**Es.**

**CREATE TABLE:** crea una nuova tabella:
```sql
CREATE TABLE studenti (
    id INT PRIMARY KEY,
    nome VARCHAR(50),
    cognome VARCHAR(50),
    età INT
);
```

**ALTER TABLE:** modifica una tabella esistente:
```sql
ALTER TABLE studenti
ADD email VARCHAR(100);
```

**DROP TABLE:** elimina una tabella:
```sql
DROP TABLE studenti;
```

**CREATE INDEX:** crea indice sulla tabella:
```sql 
CREATE INDEX idx_nome
ON studenti (nome);
```

questi comandi sono usati per gestire lo schema del database!

