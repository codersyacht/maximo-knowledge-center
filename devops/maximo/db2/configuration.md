## Maximo DB Prerequisite Configuration 

```CMD
db2 connect to MAXIMO
```
### Create TableSpaces

```CMD
db2 CREATE TABLESPACE MAXINDEX
```

```CMD
db2 CREATE TABLESPACE MAXDATA
```

### DB Sizing

```CMD
db2 update db cfg for MAXIMO using LOGFILSIZ 2048
```

```CMD
db2 update db cfg for MAXIMO using LOGPRIMARY 26
```

```CMD
db2 update db cfg for MAXIMO using LOGSECOND 24
```

## Checking the Settings

```CMD
db2 get database configuration for MAXIMO | grep LOGFILSIZ
```
```CMD
db2 get database configuration for MAXIMO | grep LOGPRIMARY
```
```CMD
db2 get database configuration for MAXIMO | grep LOGSECOND
```
