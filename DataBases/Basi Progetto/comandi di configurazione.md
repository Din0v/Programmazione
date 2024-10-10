## Common problems nel esecuzione. (FAQ)

1. su linux basta usare il commando 
```shell  
pip install psycopg2-binary
```
per risolvere il problema di psycopg2
![[Screenshot from 2023-06-24 17-51-43.png]]

2. per capire se postgres server sta girando e su quale porta:
   
```shell 
sudo service postgresql status #servizio in esecuzione
sudo netstat -lntp | grep postgres # su quale porta sta girando il servizio
```

3. per settare la password se ci da questo errore PgAdmin
```shell
sudo -u postgres psql
\password
Enter password: 

```


