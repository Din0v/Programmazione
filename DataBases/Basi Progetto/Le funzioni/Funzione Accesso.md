in questo file si gestisce il modo di accesso dei professori alla loro area riservata tramite le seguenti funzioni:

## Funzione `login`
```python
@app.route('/login')
def login():
    return render_template('/login.html')
```
Questa funzione rappresenta l'endpoint `/login`. Quando l'utente accede a questa pagina, viene restituito il template HTML `'login.html'`. 

## Funzione `autenticazione`
```python
@app.route('/autenticazione', methods=['POST'])
def autenticazione():
    log = request.form['email']
    passw = request.form['password']
    flag = False
    try:
        query = text("""SELECT email_docente, password 
                FROM docenti """)
        result = db.session.execute(query)
        for login, pasw in result:
            if (login == log and passw == pasw):
                flag = True
        if flag:
            return redirect('/valid')
        else:
            return redirect('/login')
    except DatabaseError as e:
        db.session.rollback()
        error_msg = str(e)
        return render_template('error.html', error=error_msg)
```
Questa funzione gestisce l'endpoint `/autenticazione`. Viene invocata quando l'utente invia il modulo di login tramite il metodo POST. La funzione riceve l'email e la password inserite dall'utente tramite `request.form`. 

Successivamente, viene eseguita una query SQL utilizzando la classe `text` per selezionare l'email e la password dei docenti dalla tabella `docenti`. Il risultato della query viene ottenuto utilizzando `db.session.execute(query)`. 

Viene quindi eseguito un ciclo `for` per verificare se l'email e la password inserite corrispondono a una riga della tabella dei docenti. Se si trova una corrispondenza, viene impostato il flag su `True`.

Se il flag è `True`, l'utente viene reindirizzato alla pagina `/valid`, altrimenti viene reindirizzato nuovamente alla pagina di login (`/login`).

**N.B.** un aspetto dolente di questo tipo di implementazione è che le password vengono passate in chiaro, ed è un aspetto su cui possiamo migliorare l'implementazione.

Di seguito se si verifica un errore del database di tipo `DatabaseError`, vengono annullate le modifiche al database utilizzando `db.session.rollback()`. 
Viene estratto il messaggio di errore come stringa utilizzando `str(e)` e viene restituito un template HTML di errore chiamato `'error.html'` con il messaggio di errore come parametro `error`.



## Funzione `valid`
```python
@app.route('/valid')
def valid():
    return render_template('/valid.html')
```
Questa funzione rappresenta l'endpoint `/valid`. Quando l'utente viene reindirizzato a questa pagina, viene restituito il template HTML `'valid.html'`.

## Funzione `logout`
```python
@app.route('/logout')
def logout():
    return redirect('/')
```
Questa funzione rappresenta l'endpoint `/logout`. Quando l'utente accede a questa pagina, viene reindirizzato alla homepage principale (`'/'`).

Nota: Assicurati di avere i moduli `app`, `db`, `render_template`, `request`, `redirect`, `text`, `Docenti` e `DatabaseError` correttamente importati all'inizio del codice. Inoltre, verifica che le tabelle e le variabili utilizzate nel codice siano definite e corrette nel contesto dell'applicazione.