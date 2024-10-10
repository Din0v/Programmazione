# Blocchi Atomici

è il motivo che in una tabella si ha (*nome cognome*) anzichè un unica stringa che contiene il nome e cognome (_come ho sbagliato inizialmente_). 
queste sono delle buone linee guida:

- Design appropriate data types: Choose the most appropriate data types for your attributes/columns based on the nature of the data. This helps ensure that each attribute holds a single atomic value. For example, if you have a column for **storing phone numbers**, it should be of a data type suitable for storing a **single phone number** and not a combination of phone numbers. 
(_ad esmpio_) quindi ci sara una netta distinzione tra cellulare e fisso 

- [[Normalization]]: Follow normalization principles to eliminate data redundancy and ensure atomicity. Normalization helps break down data into smaller, atomic tables, reducing the chances of data duplication and inconsistencies.


### Tags 
#Databases