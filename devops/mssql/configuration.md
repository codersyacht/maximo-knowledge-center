# MSSQL Configuration For Maximo

### Author: Jawahar

## Maximo DB Configuration

```CMD
podman exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No
```

```CMD
USE master;
```
```CMD
GO
```
```CMD
ALTER DATABASE [Maximo] ADD FILEGROUP [MAXDATA];
```
```CMD
GO
```
```CMD
ALTER DATABASE [Maximo] ADD FILEGROUP [MAXINDEX];
```
```CMD
GO
```
```CMD
ALTER DATABASE [Maximo] ADD FILE ( NAME = N'Maximo_MAXDATA', FILENAME = N'/var/opt/mssql/data/Maximo_MAXDATA.ndf', SIZE = 1024MB, FILEGROWTH = 256MB )TO FILEGROUP [MAXDATA];
```
```CMD
GO
```
```CMD
ALTER DATABASE [Maximo] ADD FILE ( NAME = N'Maximo_MAXINDEX', FILENAME = N'/var/opt/mssql/data/Maximo_MAXINDEX.ndf', SIZE = 512MB, FILEGROWTH = 128MB) TO FILEGROUP [MAXINDEX];
```
```CMD
GO
```
```CMD
ALTER DATABASE Maximo
```
```CMD
COLLATE Latin1_General_100_CI_AS_KS_SC_UTF8;
```
```CMD
GO
```
```CMD
SELECT name, collation_name FROM sys.databases WHERE name = 'Maximo';
```
```CMD
GO
```
```CMD
exit
```

## Next Step

[Configuration](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/mssql/configuration.md)
