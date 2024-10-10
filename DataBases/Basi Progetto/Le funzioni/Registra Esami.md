
La seguente documentazione spiega il funzionamento delle funzioni `registra()` e `insert()` nel codice fornito.

## Funzione `registra()`
```python
@app.route('/esami_da_registrare')
def registra():
    aggiorna_valore()
    funzioni.elimina_prove_ripetute()
    try:
        query = text("""
        SELECT ss.matricola, ss.cognome_studente, ss.nome_studente, ee.nome_esame, ROUND(AVG(ep2.voto)) AS media, ee.id_esame
        FROM esami ee
        JOIN prove pp ON ee.id_esame = pp.esame_id
        JOIN esito_prove ep2 ON pp.id_prova = ep2.prova_id
        JOIN studenti ss ON ss.matricola = ep2.studente_id
        WHERE ee.num_prove = (
            SELECT COUNT(p.id_prova)
            FROM esami e
            JOIN prove p ON e.id_esame = p.esame_id
            JOIN esito_prove ep ON p.id_prova = ep.prova_id
            JOIN studenti s ON s.matricola = ep.studente_id
            WHERE ep.validita AND s.matricola = ss.matricola
            GROUP BY matricola)
        ::integer
        GROUP BY ss.matricola, ee.nome_esame, ee.id_esame
        """)
        result = db.session.execute(query)
        results = []
        for row in result:
            results.append(row)
        return render_template('esami_da_registrare.html', results=results)
    except DatabaseError as e:
        db.session.rollback()
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
```

Questa funzione gestisce l'endpoint `/esami_da_registrare`. Quando l'utente accede a questa pagina, viene eseguito il seguente processo:

1. Viene chiamata la funzione `aggiorna_valore()`. Questa funzione non è definita nel codice fornito, quindi è necessario verificare il suo funzionamento e implementazione in un modulo esterno.

2. Viene chiamata la funzione `funzioni.elimina_prove_ripetute()`. Questa funzione fa parte del modulo `funzioni` definito nel codice. Assicurati che il modulo `funzioni` sia correttamente importato all'inizio del codice e che la funzione `elimina_prove_ripetute()` sia definita nel modulo.

3. Viene eseguito il blocco `try` per gestire eventuali eccezioni di tipo `DatabaseError`. Se si verifica un errore del database, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

4. Viene eseguita una complessa query SQL per selezionare gli esami che devono essere registrati dagli studenti. La query utilizza diverse tabelle (esami, prove, esito_prove, studenti) e applica criteri di filtro e raggruppamento per ottenere i risultati desiderati. I risultati vengono salvati in una lista chiamata `results`.

5. Infine, viene restituito un template HTML chiamato `'esami

_da_registrare.html'` insieme ai risultati ottenuti. Il template può utilizzare i dati forniti nella variabile `results` per visualizzarli nel modo desiderato.

## Funzione `insert()`
```python
@app.route('/insert', methods=['POST'])
def insert():
    try:
        studente_id = request.form.get('matricola')
        esame_id = request.form.get('id_esame')
        voto = request.form.get('voto')
        data = datetime.now().date()
        lode = funzioni.str_to_bool(request.form.get('lode'))
        
        nuovo_esame = Esami_superati(voto, lode, data, studente_id, esame_id)
        db.session.add(nuovo_esame)
        db.session.commit()
    except DatabaseError as e:
        db.session.rollback()
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
    
    try:
        query = text("""
        SELECT  ep.id_superamento
        FROM esami e
        JOIN prove  p ON p.esame_id = e.id_esame
        JOIN esito_prove ep ON p.id_prova = ep.prova_id
        JOIN studenti s ON s.matricola = ep.studente_id 
        WHERE e.id_esame = :esame_id and s.matricola = :studente_id and ep.validita=True 
        """)
    
        indici_prove = db.session.execute(query.params(esame_id=esame_id, studente_id=studente_id))
    
        db.session.commit()
    except DatabaseError as e:
        db.session.rollback()
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
    
    try:
        for idx in indici_prove:    
            query = text("""
            UPDATE esito_prove 
            SET validita = False 
            WHERE id_superamento = :id_superamento
            """)
        
            db.session.execute(query, {"id_superamento": idx.id_superamento})
        db.session.commit()
        return redirect('/esami_da_registrare')      
    except DatabaseError as e:
        db.session.rollback()
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
```

Questa funzione gestisce l'endpoint `/insert` e viene invocata quando viene inviato un metodo POST a tale endpoint. Il processo eseguito da questa funzione è il seguente:

1. Viene eseguito il blocco `try` per gestire eventuali eccezioni di tipo `DatabaseError`. Se si verifica un errore del database, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

2. Vengono acquisiti i valori dei parametri dal form inviato con la richiesta POST. In particolare, vengono memorizzati i valori della matricola dello studente (`studente_id`), l'ID dell'esame (`esame_id`), il voto dello studente (`voto`), la data corrente (`data`) e un valore booleano (`lode`) ottenuto convertendo la stringa fornita dal form in un booleano utilizzando la funzione `funzioni.str_to_bool()` definita nel modulo `funzioni`. Assicurati

 che il modulo `funzioni` sia correttamente importato all'inizio del codice e che la funzione `str_to_bool()` sia definita nel modulo.

3. Viene creato un nuovo oggetto `Esami_superati` utilizzando i valori ottenuti dal form.

4. L'oggetto `nuovo_esame` viene aggiunto alla sessione del database utilizzando `db.session.add(nuovo_esame)`.

5. Viene eseguito il commit delle modifiche al database utilizzando `db.session.commit()`.

6. Viene eseguito un altro blocco `try` per gestire eventuali eccezioni di tipo `DatabaseError` durante l'esecuzione della query successiva. Se si verifica un errore del database, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

7. Viene eseguita una query per ottenere gli indici delle prove associate all'esame (`esame_id`) e allo studente (`studente_id`) che hanno la validità impostata su `True`.

8. Viene eseguito il commit delle modifiche al database utilizzando `db.session.commit()`.

9. Viene eseguito un altro blocco `try` per gestire eventuali eccezioni di tipo `DatabaseError` durante l'aggiornamento delle prove. Se si verifica un errore del database, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

10. Per ogni indice di prova (`idx`) ottenuto dalla query precedente, viene eseguita un'ulteriore query per aggiornare il campo `validita` a `False` nell'oggetto `Esito_prove` corrispondente utilizzando l'indice `id_superamento`.

11. Viene eseguito il commit delle modifiche al database utilizzando `db.session.commit()`.

12. Infine, l'utente viene reindirizzato alla pagina `/esami_da_registrare` utilizzando `redirect('/esami_da_registrare')`.