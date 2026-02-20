# MSSQL Setup

### Author: Jawahar

## Prerequisite

Docker setup. To install docker follow the instructions [here](https://github.com/codersyacht/knowledge-center/blob/main/system/Docker_Installation_General.md)

## Install MSSQL

docker pull mcr.microsoft.com/mssql/rhel/server:2022-latest
 

docker run -d --name sql2022 --hostname sql2022 -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=LabMachine4@Training" -e "MSSQL_PID=Developer" -p 1433:1433 mcr.microsoft.com/mssql/server:2022-latest




docker exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No


docker exec -it sql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "LabMachine4@Training" -No


CREATE DATABASE MyTestDB;
GO


jdbc:sqlserver://9.30.87.54:1433;databaseName=MyTestDB;



SELECT DISTINCT TABLE_SCHEMA FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_NAME = 'MAXOBJECT';


SELECT TABLE_SCHEMA, TABLE_NAME FROM sys.tables WHERE TABLE_NAME = 'MAXOBJECT'
