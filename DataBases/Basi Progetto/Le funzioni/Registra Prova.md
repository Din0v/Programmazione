La seguente documentazione spiega il modo di funzionamento delle funzioni presenti nel codice fornito:

## Funzione `registrazione_prova()`
```python
@app.route('/registrazione_prova')
def registrazione_prova():
    try:
        today = datetime.now().date()
        query = text("""
                SELECT s.*, p.id_prova, p.tipo_prova, a.data_appello
                FROM studenti s
                JOIN iscrizioni i ON s.matricola = i.studente_id
                JOIN appelli a ON a.id_appello = i.appello_id
                JOIN prove p ON a.prova_id = p.id_prova 
                LEFT JOIN esito_prove ep ON i.appello_id = ep.prova_id AND s.matricola = ep.studente_id
                WHERE ep.voto IS NULL AND a.data_appello < :today
                 """)
        result = db.session.execute(query, {"today": today})
        return render_template('/registrazione_prova.html', result=result)
    except DatabaseError as e:
        db.session.rollback()
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
```

Questa funzione gestisce l'endpoint `/registrazione_prova` e viene invocata quando un utente accede a tale endpoint. Il processo eseguito da questa funzione è il seguente:

1. Viene eseguito il blocco `try` per gestire eventuali eccezioni di tipo `DatabaseError`. Se si verifica un errore del database, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

2. Viene acquisita la data corrente utilizzando `datetime.now().date()` e memorizzata nella variabile `today`.

3. Viene eseguita una query per selezionare gli studenti (`studenti s`) che sono iscritti a un appello di prova (`appelli a`) e che hanno ancora un esito di prova nullo (`esito_prove ep.voto IS NULL`). Inoltre, viene verificato che la data dell'appello sia precedente alla data corrente (`a.data_appello < :today`). La query restituisce i dati dello studente (`s.*`), l'ID della prova (`p.id_prova`), il tipo di prova (`p.tipo_prova`) e la data dell'appello (`a.data_appello`).

4. Viene eseguito `db.session.execute()` per eseguire la query utilizzando i parametri `{"today": today}`.

5. I risultati ottenuti dalla query vengono passati al template HTML chiamato `'registrazione_prova.html'` utilizzando `render_template()`. I risultati sono disponibili nella variabile `result` nel template.

6. Il template può utilizzare i dati forniti nella variabile `result` per visualizzarli nel modo desiderato.

7. Se si verifica un errore del database durante l'esecuzione della query, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio

 di errore come parametro `error`.

## Funzione `reg_prova()`
```python
@app.route('/reg_prova', methods=['POST'])
def reg_prova():
    matr = request.form.get("matricola")
    nome = request.form.get("nome")
    cognome = request.form.get("cognome")
    id_prova = int(request.form.get("id_prova"))
    
    return render_template('/reg_prova.html', matr=matr, nome=nome, cognome=cognome, id_prova=id_prova)
```

Questa funzione gestisce l'endpoint `/reg_prova` e viene invocata quando viene inviato un modulo tramite il metodo POST a tale endpoint. Il processo eseguito da questa funzione è il seguente:

1. Vengono acquisiti i valori dei campi del modulo tramite `request.form.get()`. I campi includono "matricola", "nome", "cognome" e "id_prova".

2. Viene restituito un template HTML chiamato `'reg_prova.html'`, passando i valori acquisiti come parametri `matr`, `nome`, `cognome` e `id_prova`.

## Funzione `ins_prova_superata()`
```python
@app.route('/ins_prova_superata', methods=['POST'])
def ins_prova_superata():
    try:
        matr = request.form.get("matricola")
        id_prova = int(request.form.get("id_prova"))
        voto = int(request.form.get("voto_prova"))
        validita = funzioni.str_to_bool(request.form.get("validita"))
        data_scadenza = request.form.get("data_scadenza")
        new_reg_prova = Esito_prove(voto, validita, data_scadenza, id_prova, matr)
        db.session.add(new_reg_prova)
        db.session.commit()
        return redirect('/registrazione_prova')
    except DatabaseError as e:
        db.session.rollback() 
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
```

Questa funzione gestisce l'endpoint `/ins_prova_superata` e viene invocata quando viene inviato un modulo tramite il metodo POST a tale endpoint. Il processo eseguito da questa funzione è il seguente:

1. Viene eseguito il blocco `try` per gestire eventuali eccezioni di tipo `DatabaseError`. Se si verifica un errore del database, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. Viene quindi estratto il messaggio di errore come stringa utilizzando `str(e)`. Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

2. Vengono acquisiti i valori dei campi del modulo tramite `request.form.get()`. I campi includono "matricola", "id_prova", "voto_prova", "validita" e "data_scadenza".

3. Viene convertito il valore del campo "voto_prova" in un intero utilizzando `int()`.

4. Viene chiamata la funzione `funzioni.str_to_bool()` per convertire il valore del campo "validita" in un valore booleano.

5. Viene creato un nuovo oggetto `Esito_prove` utilizzando i valori ottenuti dal modulo.

6. L'oggetto `new_reg_prova` viene aggiunto alla sessione del database utilizzando `db.session.add()`.

7. Le modifiche vengono confermate e salvate nel database utilizzando `db.session.commit()`.

8. Viene reindirizzato l'utente alla pagina '/registrazione_prova' utilizzando `redirect()`.

9. Se si verifica un errore del database durante l'aggiunta o il commit dell'oggetto, vengono annullate le modifiche al database utilizzando `db.session.rollback()`.
   Viene  estratto il messaggio di errore come stringa utilizzando `str(e)`. 
   Viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.

Questa documentazione fornisce una panoramica sul modo di funzionamento delle funzioni presenti nel codice fornito.