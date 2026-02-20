# MSSQL Setup

### Author: Jawahar

## Prerequisite

Docker setup. To install docker follow the instructions [here](https://github.com/codersyacht/knowledge-center/blob/main/system/Docker_Installation_General.md)

## Install MSSQL

```CMD
docker pull mcr.microsoft.com/mssql/server:2022-latest
 ```
```CMD
docker run -d --name sql2022 --hostname sql2022 -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=LabMachine4@Training" -e "MSSQL_PID=Developer" -p 1433:1433 mcr.microsoft.com/mssql/server:2022-latest
```

For MQSQL command code, execute the following command

```CMD
docker exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No
```
