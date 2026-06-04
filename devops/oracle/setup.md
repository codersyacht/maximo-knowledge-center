
```CMD
podman pull container-registry.oracle.com/database/free:23.26.2.0-arm64
```
```CMD
podman run -d --name oracle-maximo -p 1521:1521 -p 5500:5500 -e ORACLE_PWD=LabMachine4@Training  container-registry.oracle.com/database/free:23.26.2.0-arm64
```
```CMD
podman logs -f oracle-maximo
```
```CMD
podman exec -it oracle-maximo sqlplus / as sysdba
```
```CMD
ALTER PLUGGABLE DATABASE FREEPDB1 CLOSE IMMEDIATE;
```
```CMD
DROP PLUGGABLE DATABASE FREEPDB1 INCLUDING DATAFILES;
```
```CMD
CREATE PLUGGABLE DATABASE OMDB ADMIN USER pdbadmin IDENTIFIED BY YourSecurePassword FILE_NAME_CONVERT=('/opt/oracle/oradata/FREE/pdbseed/', '/opt/oracle/oradata/FREE/OMDB/');
```
```CMD
ALTER PLUGGABLE DATABASE OMDB OPEN READ WRITE;
```
```CMD
ALTER PLUGGABLE DATABASE ALL SAVE STATE;
```
```CMD
ALTER SESSION SET CONTAINER = OMDB;
```
```CMD
ALTER SYSTEM SET nls_length_semantics = CHAR SCOPE = BOTH;
```
```CMD
ALTER SYSTEM SET open_cursors = 1000 SCOPE = BOTH;
```
```CMD
ALTER SYSTEM SET cursor_sharing = FORCE SCOPE = BOTH;
```
```CMD
CREATE TABLESPACE maxdata DATAFILE 'maxdata.dbf' SIZE 1000M AUTOEXTEND ON NEXT 100M MAXSIZE UNLIMITED;
```
```CMD
CREATE TABLESPACE maxindex DATAFILE 'maxindex.dbf' SIZE 500M AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```
```CMD
CREATE USER maximo  IDENTIFIED BY "LabMachine4@Training" DEFAULT TABLESPACE maxdata TEMPORARY TABLESPACE maxtemp QUOTA UNLIMITED ON maxdata QUOTA UNLIMITED ON maxindex;
```
```CMD
GRANT ALL PRIVILEGES TO maximo;
```
```CMD
GRANT DBA TO maximo;
```
```CMD
@?/ctx/admin/catctx.sql change_on_install SYSAUX TEMP NO;
```
```CMD
@?/ctx/admin/defaults/drdefus.sql;
```
```CMD
GRANT EXECUTE ON ctxsys.ctx_ddl TO maximo;
```

