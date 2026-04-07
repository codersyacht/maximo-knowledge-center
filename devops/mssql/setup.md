# MSSQL Setup

### Author: Jawahar

## Prerequisite

Install Podman.

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


## Update MSSQL Server Container and Install FTS (Full Text Search)

```CMD
docker exec -u 0 -it sql2022 bash
```
```CMD
apt-get update
```
```CMD
apt-get install -y curl apt-transport-https gnupg
```
```CMD
curl -sSL https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
```
```CMD
curl -sSL https://packages.microsoft.com/config/ubuntu/22.04/mssql-server-2022.list -o /etc/apt/sources.list.d/mssql-server-2022.list
```
```CMD
apt-get update
```
```CMD
apt-get install -y mssql-server-fts
```
```CMD
exit
```

## Restart Container

```CMD
docker stop sql2022
```
```
docker start sql2022
```
```CMD
docker exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No
```
```CMD
SELECT FULLTEXTSERVICEPROPERTY('IsFullTextInstalled');
```
```
GO
```
Output should be 1.
