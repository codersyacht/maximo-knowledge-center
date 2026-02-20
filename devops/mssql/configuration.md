# MSSQL Configuration For Maximo

### Author: Jawahar

## Maximo DB Configuration

```CMD
docker exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No
```

```CMD

USE master;

ALTER DATABASE [Maximo] ADD FILEGROUP [MAXDATA];
GO

ALTER DATABASE [Maximo] ADD FILEGROUP [MAXINDEX];
GO

ALTER DATABASE [Maximo] ADD FILE ( NAME = N'Maximo_MAXDATA', FILENAME = N'/var/opt/mssql/data/Maximo_MAXDATA.ndf', SIZE = 1024MB, FILEGROWTH = 256MB )TO FILEGROUP [MAXDATA];
GO

ALTER DATABASE [Maximo] ADD FILE ( NAME = N'Maximo_MAXINDEX', FILENAME = N'/var/opt/mssql/data/Maximo_MAXINDEX.ndf', SIZE = 512MB, FILEGROWTH = 128MB) TO FILEGROUP [MAXINDEX];
GO

exit

```
