
## Funzione `prove_superate`
```python
@app.route('/prove_superate')
def prove_superate():
    aggiorna_valore()
    funzioni.elimina_prove_ripetute()
    try:
        results = db.session.query(Studenti.matricola, Studenti.cognome_studente, Studenti.nome_studente, Esami.nome_esame, 
                               Esito_prove.voto, Appelli.data_appello, Esito_prove.data_scadenza, Prove.tipo_prova,Esito_prove.validita)\
        .join(Esito_prove, Studenti.matricola==Esito_prove.studente_id)\
        .join(Prove, Prove.id_prova==Esito_prove.prova_id)\
        .join(Esami, Esami.id_esame==Prove.esame_id)\
        .join(Appelli, Appelli.prova_id == Prove.id_prova)\
        .filter(Esito_prove.validita)\
        .order_by(Studenti.matricola)\
        .all()
        return render_template('prove_superate.html', results=results)
    except DatabaseError as e:
        db.session.rollback()
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
```

Questa funzione gestisce l'endpoint `/prove_superate`. Quando l'utente accede a questa pagina, viene eseguito il seguente processo:


> [!warning]
> 1. Viene chiamata la funzione `aggiorna_valore()`. Questa funzione non è definita nel codice fornito, quindi è necessario verificare il suo funzionamento e implementazione in un modulo esterno.

2. Viene chiamata la funzione `funzioni.elimina_prove_ripetute()`. Questa funzione fa parte del modulo `funzioni` definito precedentemente. 

3. Viene eseguito il blocco `try` per gestire eventuali eccezioni di tipo `DatabaseError`. Se si verifica un errore del database, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. 
   Viene estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

4. Viene eseguita una query SQL complessa che recupera le informazioni relative alle prove superate dai studenti. La query utilizza il metodo `query()` di `db.session` e la sintassi di SQLAlchemy per creare una query composta che coinvolge diverse tabelle (Studenti, Esito_prove, Prove, Esami, Appelli). La query seleziona vari campi di interesse e applica anche alcuni criteri di filtro e ordinamento.

5. I risultati della query vengono restituiti come un elenco di tuple. Ogni tupla rappresenta una riga di dati contenente le informazioni sullo studente, l'esame, l'esito della prova, la data dell'appello e altre informazioni correlate.

6. Infine, i risultati vengono passati al template HTML `'prove_superate.html'` come parametro `results` utilizzando la funzione `render_template()`. Il template HTML può quindi utilizzare questi dati per visualizzarli nel modo desiderato.

