
## Prerequisite

```CMD
podman machine init --cpus 4 --memory 4096 --disk-size 40
```
```CMD
podman machine start
```

```CMD
podman pull container-registry.oracle.com/database/free:23.26.2.0-arm64
```
```CMD
podman run -d --name ORADB -p 1521:1521 -p 5500:5500 -e ORACLE_PWD=LabMachine4@Training  container-registry.oracle.com/database/free:23.26.2.0-arm64
```
```CMD
podman logs -f ORADB
```
```CMD
podman exec -it ORADB sqlplus / as sysdba
```
```CMD
ALTER PLUGGABLE DATABASE FREEPDB1 CLOSE IMMEDIATE;
```
```CMD
DROP PLUGGABLE DATABASE FREEPDB1 INCLUDING DATAFILES;
```
```CMD
CREATE PLUGGABLE DATABASE MAXIMO ADMIN USER pdbadmin IDENTIFIED BY password FILE_NAME_CONVERT=('/opt/oracle/oradata/FREE/pdbseed/', '/opt/oracle/oradata/FREE/appdb/');
```
```CMD
ALTER PLUGGABLE DATABASE MAXIMO OPEN READ WRITE;
```
```CMD
ALTER PLUGGABLE DATABASE ALL SAVE STATE;
```
```CMD
ALTER SESSION SET CONTAINER = MAXIMO;
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
CREATE TABLESPACE MAXDATA DATAFILE 'maxdata.dbf' SIZE 1000M AUTOEXTEND ON NEXT 100M MAXSIZE UNLIMITED;
```
```CMD
CREATE TABLESPACE MAXINDX DATAFILE 'maxindx.dbf' SIZE 500M AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```
```CMD
CREATE TEMPORARY TABLESPACE MAXTEMP TEMPFILE 'maxtemp.dbf' SIZE 500M AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```
```
CREATE TABLESPACE MAXLOBS DATAFILE 'maxlobs.dbf' SIZE 512M AUTOEXTEND ON NEXT 100M MAXSIZE UNLIMITED EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO;
```
```CMD
CREATE USER maximo IDENTIFIED BY "LabMachine4@Training" DEFAULT TABLESPACE MAXDATA TEMPORARY TABLESPACE MAXTEMP QUOTA UNLIMITED ON MAXDATA QUOTA UNLIMITED ON MAXINDX QUOTA UNLIMITED ON MAXLOBS;
```
```CMD
GRANT ALL PRIVILEGES TO maximo;
```
```CMD
GRANT DBA TO maximo;
```

```CMD
ALTER SESSION SET CONTAINER = CDB$ROOT;
```
```CMD
ALTER SYSTEM SET processes = 500 SCOPE=SPFILE;
```
```CMD
ALTER SYSTEM SET sessions = 1000 SCOPE=SPFILE;
```
```CMD
ALTER SYSTEM SET session_cached_cursors = 500 SCOPE=SPFILE;
```
```CMD
SHUTDOWN IMMEDIATE;
```
```CMD
STARTUP;
```
```CMD
ALTER SESSION SET CONTAINER = MAXIMO;
```
```CMD
ALTER SYSTEM SET nls_length_semantics = CHAR SCOPE=SPFILE;
```
```CMD
ALTER SYSTEM SET open_cursors = 1000 SCOPE=BOTH;
```
```CMD
ALTER SYSTEM SET cursor_sharing = FORCE SCOPE=BOTH;
```
```CMD
ALTER SYSTEM SET undo_retention = 900 SCOPE=BOTH;
```
```CMD
ALTER SYSTEM SET nls_date_format = 'YYYY-MM-DD HH24:MI:SS' SCOPE=SPFILE;
```
```CMD
ALTER SYSTEM SET nls_language = 'AMERICAN' SCOPE=SPFILE;
```
```CMD
ALTER SYSTEM SET nls_territory = 'AMERICA' SCOPE=SPFILE;
```
```CMD
ALTER PLUGGABLE DATABASE MAXIMO CLOSE;
```
```CMD
ALTER PLUGGABLE DATABASE MAXIMO OPEN;
```
```CMD
CONNECT maximo/"LabMachine4@Training"@//localhost:1521/MAXIMO
```
```CMD
CONNECT / AS SYSDBA
```
```CMD
ALTER SESSION SET "_ORACLE_SCRIPT" = TRUE;

```
```CMD
ALTER SESSION SET CONTAINER = MAXIMO;

```
```CMD
ALTER SESSION SET "_ORACLE_SCRIPT" = TRUE;

```
```CMD
@?/ctx/admin/catctx.sql change_on_install SYSAUX TEMP NO
```
```CMD
SELECT comp_name, status FROM dba_registry WHERE comp_name = 'Oracle Text';
```
```SQL
SELECT comp_name, status FROM dba_registry WHERE comp_name = 'Oracle Text';
```
```CMD
@?/ctx/admin/catctx.sql change_on_install SYSAUX TEMP NO;
```
```
BEGIN
  ctx_ddl.create_preference('MAXIMO_STORAGE', 'BASIC_STORAGE');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'I_TABLE_CLAUSE', 'tablespace MAXDATA LOB(token_info) store as (tablespace MAXLOBS enable storage in row)');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'I_INDEX_CLAUSE', 'tablespace MAXINDX compress 2');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'K_TABLE_CLAUSE', 'tablespace MAXINDX');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'R_TABLE_CLAUSE', 'tablespace MAXDATA LOB(data) store as (tablespace MAXLOBS cache)');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'N_TABLE_CLAUSE', 'tablespace MAXINDX');
END;
/
```
```CMD
GRANT EXECUTE ON ctxsys.ctx_ddl TO maximo;
```

