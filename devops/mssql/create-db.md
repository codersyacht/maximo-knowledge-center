# Create DB Maximo

### Author: Jawahar

Login to MSSQL command mode using the following command:

```CMD
podman exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No
```

In SQL command mode, execute the following 3 commands.

```CMD
USE master;
```
```CMD
CREATE DATABASE Maximo;
```
```CMD
GO
```

## Client Connection Details

| Field                | Value                                                              |
|----------------------|--------------------------------------------------------------------|
| Host                 | 9.30.87.54                                                         |
| Database/Schema Name | Maximo                                                             |
| Port                 | 1433                                                               |
| Username             | sa                                                                 |
| Password             | LabMachine4@Training                                               |
| JDBC URL             | jdbc:sqlserver://9.30.87.54:1433;databaseName=Maximo;              |

## Next Step

[Configuration](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/mssql/configuration.md)
