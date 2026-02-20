# Create DB Maximo

### Author: Jawahar

Login to MSSQ_ command mode using the following command:

```CMD
docker exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No
```

In SQL command mode, execute the following 2 commands.

```CMD
CREATE DATABASE Maximo;
```
```CMD
GO
```


jdbc:sqlserver://9.30.87.54:1433;databaseName=MyTestDB;



SELECT DISTINCT TABLE_SCHEMA FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_NAME = 'MAXOBJECT';


SELECT TABLE_SCHEMA, TABLE_NAME FROM sys.tables WHERE TABLE_NAME = 'MAXOBJECT'
