## Creating and Deleting DB

### Create DB MAXIMO

If DB2 is not yet installed, then following the below link to set it up. <br>
[DB2 Installation](https://github.com/codersyacht/private/blob/main/db2/Setup.md)

Login to the machine with the db2 user (db2inst1). <br>

Access db2 console by type **db2**.

Execute the following command:

```CMD
db2 CREATE DATABASE MAXIMO AUTOMATIC STORAGE YES USING CODESET UTF-8 TERRITORY DEFAULT COLLATE USING SYSTEM PAGESIZE 32768
```
If success, following message will be displayed.

DB20000I  The CREATE DATABASE command completed successfully. <br>

quit.


### Delete DB MAXIMO

```CMD
db2 drop db MAXIMO
```
