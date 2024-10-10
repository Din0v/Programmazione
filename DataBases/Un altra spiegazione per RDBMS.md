[[RDBMS]]

In a relational database, data is stored in multiple related tables, and the relationships between these tables are defined by establishing common columns between them. These relationships allow data to be linked and retrieved efficiently. The relational database model offers several key concepts:

1.  [[Tables]] : Data in a relational database is organized into tables, also known as relations. Each table consists of rows (also called tuples or records) and columns (also called attributes or fields). Rows represent individual instances of data, while columns represent the specific attributes or properties of the data.

2.  [[Keys]]: Each table typically has one or more columns that uniquely identify each row. These columns are called primary keys and ensure the uniqueness of the data within the table. Primary keys are used to establish relationships with other tables through foreign keys, which are columns in one table that refer to the primary key of another table.
   
3.  [[Relationships]] : Relationships are established between tables using foreign keys. They define the associations and dependencies between entities or data elements in different tables. Common types of relationships include one-to-one, one-to-many, and many-to-many relationships.
   
4.  [[Normalization]]: Relational databases employ a process called normalization to eliminate redundancy and ensure data integrity. Normalization involves breaking down data into smaller, more manageable tables and removing data duplication. This helps reduce inconsistencies and improves efficiency in data storage and updates.
   
5.  [[Query Language]]: Relational databases use a standardized query language called Structured Query Language (SQL) to interact with the database. SQL allows users to perform various operations such as retrieving, inserting, updating, and deleting data from the database tables.



### Tags 
#Databases