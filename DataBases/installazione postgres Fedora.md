# Fedora 
```Bash 
$ sudo dnf install postgresql postgresql-server    # install client/server
$ sudo postgresql-setup --initdb --unit postgresql # initialize PG cluster
$ sudo systemctl start postgresql                  # start cluster
$ sudo su - postgres                               # login as DB admin
$ createdb quick-start                             # create testing database
$ psql -d quick-start                              # connect to the new database
```





### Tags
#Databases 