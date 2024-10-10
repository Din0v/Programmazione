# using virtual env 

## Passo 1
```Bash
pip install virtualenv 
```

## Passo 2 
```Bash 
virtualenv Proggetto_Virtuale
```
cosi si crea un ambiente virtuale .

## Passo 3 
attivare l'ambiente virutale di lavoro

```Bash
source Progetto_virtuale/bin/activate 
```

usando  il commando: 

```Bash 
pip list 
```

darà un risultato simile a questo:
![[Pasted image 20230517155228.png]]

## Passo 4 
per deattivare l'ambiente virutale base usare il commando: 

```Bash 
deactivate 
```

![[Pasted image 20230517155744.png]]

## Passo 5 
generare un file locale con tutti i requisiti del determinato ambiente virtuale creato da noi: 

``` Bash 
pip freeze --local > requirements.txt
```

the command **pip freeze** outputs all installed modules (including version numbers). The `--local` flag prevents Pip from printing globally installed packages in a virtual environment.

### **NB**

per vedere quale ambiente stiamo utlizzando basta scrivere:
```Bash
which python
```
ed il risutlato sarà: 

![[Pasted image 20230517155936.png]]





### Tags
#Databases 
