
# Oracle Installation

### Author: Mohamed Jawahar Hussain

## Introduction

Oracle 23 Installation and Configuration for Maximo.

## Prerequisite

**Linux**

[Install Docker](/devops/system/docker-installation.md)


## Install Oracle Container

**Mac**

**Note:**
Run the below two commands to use the preconfigured Oracle container. In such case you do not need to run any further steps. You may exit.
Run the third command if you want to set up oracle from the beginning. Follow all the following steps further.

```CMD
podman run -d --name oracleserver -p 1521:1521 -p 5500:5500 -e ORACLE_PWD=LabMachine4@Training docker.io/codersyacht/maximo-oracle-mac:base
```
```CMD
podman pull container-registry.oracle.com/database/free:23.26.2.0-arm64
```
```CMD
podman run -d --name oracleserver -p 1521:1521 -p 5500:5500 -e ORACLE_PWD=LabMachine4@Training container-registry.oracle.com/database/free:23.26.2.0-arm64
```
**Linux**

**Note:**
Run the below two commands to use the preconfigured Oracle container. In such case you do not need to run any further steps. You may exit.
Run the third command if you want to set up oracle from the beginning. Follow all the following steps further.

```CMD
docker pull docker.io/codersyacht/maximo-oracle-linux:base
```
```CMD
docker run -d --name oracleserver -p 1521:1521 -p 5500:5500 -e ORACLE_PWD=LabMachine4@Training docker.io/codersyacht/maximo-oracle-linux:base
```

```CMD
docker pull container-registry.oracle.com/database/free:latest
```
```CMD
docker run -d --name oracleserver -p 1521:1521 -p 5500:5500 -e ORACLE_PWD=LabMachine4@Training  container-registry.oracle.com/database/free:latest
```
### Review Logs

```CMD
docker logs -f ORADB
```

### Connect as SYSDBA

```CMD
docker exec -it ORADB sqlplus / as sysdba
```

### Delete Existing Default DB FREEPDB1 (Optional Step)

```CMD
ALTER PLUGGABLE DATABASE FREEPDB1 CLOSE IMMEDIATE;
```
```CMD
DROP PLUGGABLE DATABASE FREEPDB1 INCLUDING DATAFILES;
```
### Create & Configure Database Maximo

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
ALTER SYSTEM SET nls_length_semantics = CHAR SCOPE = BOTH;
```
```CMD
ALTER SYSTEM SET open_cursors = 1000 SCOPE = BOTH;
```
```CMD
ALTER SYSTEM SET cursor_sharing = FORCE SCOPE = BOTH;
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

### Create Tablespaces for Maximo

```CMD
CREATE TABLESPACE MAXDATA DATAFILE 'maxdata.dbf' SIZE 1000M AUTOEXTEND ON NEXT 100M MAXSIZE UNLIMITED;
```
```CMD
CREATE TABLESPACE MAXINDEX DATAFILE 'maxindex.dbf' SIZE 500M AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```
```CMD
CREATE TEMPORARY TABLESPACE MAXTEMP TEMPFILE 'maxtemp.dbf' SIZE 500M AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```
```
CREATE TABLESPACE MAXLOBS DATAFILE 'maxlobs.dbf' SIZE 512M AUTOEXTEND ON NEXT 100M MAXSIZE UNLIMITED EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO;
```

### Create User maximo & Grant Access

```CMD
CREATE USER maximo IDENTIFIED BY "LabMachine4@Training" DEFAULT TABLESPACE MAXDATA TEMPORARY TABLESPACE MAXTEMP QUOTA UNLIMITED ON MAXDATA QUOTA UNLIMITED ON MAXINDEX QUOTA UNLIMITED ON MAXLOBS;
```
```CMD
GRANT ALL PRIVILEGES TO maximo;
```
```CMD
GRANT DBA TO maximo;
```

### Install Oracle Text

```CMD
ALTER SESSION SET "_ORACLE_SCRIPT" = TRUE;
```

//```CMD
//ALTER SESSION SET CONTAINER = MAXIMO;
//```

```CMD
@?/ctx/admin/catctx.sql change_on_install SYSAUX TEMP NO
```
```CMD
SELECT comp_name, status FROM dba_registry WHERE comp_name = 'Oracle Text';
```

```
BEGIN
  ctx_ddl.create_preference('MAXIMO_STORAGE', 'BASIC_STORAGE');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'I_TABLE_CLAUSE', 'tablespace MAXDATA LOB(token_info) store as (tablespace MAXLOBS enable storage in row)');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'I_INDEX_CLAUSE', 'tablespace MAXINDEX compress 2');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'K_TABLE_CLAUSE', 'tablespace MAXINDEX');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'R_TABLE_CLAUSE', 'tablespace MAXDATA LOB(data) store as (tablespace MAXLOBS cache)');
  ctx_ddl.set_attribute('MAXIMO_STORAGE', 'N_TABLE_CLAUSE', 'tablespace MAXINDEX');
END;
/
```
```CMD
GRANT EXECUTE ON ctxsys.ctx_ddl TO maximo;
```
```CMD
grant select_catalog_role to maximo;
```

### Configure multi-language lexers + finalize

```CMD
call ctx_ddl.drop_preference('global_lexer');
call ctx_ddl.drop_preference('default_lexer');
call ctx_ddl.drop_preference('english_lexer');
call ctx_ddl.drop_preference('chinese_lexer');
call ctx_ddl.drop_preference('japanese_lexer');
call ctx_ddl.drop_preference('korean_lexer');
call ctx_ddl.drop_preference('german_lexer');
call ctx_ddl.drop_preference('dutch_lexer');
call ctx_ddl.drop_preference('swedish_lexer');
call ctx_ddl.drop_preference('french_lexer');
call ctx_ddl.drop_preference('italian_lexer');
call ctx_ddl.drop_preference('spanish_lexer');
call ctx_ddl.drop_preference('portu_lexer');
call ctx_ddl.create_preference('default_lexer','basic_lexer');
call ctx_ddl.create_preference('english_lexer','basic_lexer');
call ctx_ddl.create_preference('chinese_lexer','chinese_lexer');
call ctx_ddl.create_preference('japanese_lexer','japanese_lexer');
call ctx_ddl.create_preference('korean_lexer','korean_morph_lexer');
call ctx_ddl.create_preference('german_lexer','basic_lexer');
call ctx_ddl.create_preference('dutch_lexer','basic_lexer');
call ctx_ddl.create_preference('swedish_lexer','basic_lexer');
call ctx_ddl.create_preference('french_lexer','basic_lexer');
call ctx_ddl.create_preference('italian_lexer','basic_lexer');
call ctx_ddl.create_preference('spanish_lexer','basic_lexer');
call ctx_ddl.create_preference('portu_lexer','basic_lexer');
call ctx_ddl.create_preference('global_lexer', 'multi_lexer');
call ctx_ddl.add_sub_lexer('global_lexer','default','default_lexer');
call ctx_ddl.add_sub_lexer('global_lexer','english','english_lexer','en');
call ctx_ddl.add_sub_lexer('global_lexer','simplified chinese','chinese_lexer','zh');
call ctx_ddl.add_sub_lexer('global_lexer','japanese','japanese_lexer',null);
call ctx_ddl.add_sub_lexer('global_lexer','korean','korean_lexer',null);
call ctx_ddl.add_sub_lexer('global_lexer','german','german_lexer','de');
call ctx_ddl.add_sub_lexer('global_lexer','dutch','dutch_lexer',null);
call ctx_ddl.add_sub_lexer('global_lexer','swedish','swedish_lexer','sv');
call ctx_ddl.add_sub_lexer('global_lexer','french','french_lexer','fr');
call ctx_ddl.add_sub_lexer('global_lexer','italian','italian_lexer','it');
call ctx_ddl.add_sub_lexer('global_lexer','spanish','spanish_lexer','es');
call ctx_ddl.add_sub_lexer('global_lexer','portuguese','portu_lexer',null);
```
```CMD
@?/ctx/admin/defaults/drdefus.sql;
```
### Commit & Exit SQLplus

```CMD
commit;
```
```CMD
ALTER SESSION SET CONTAINER = CDB$ROOT;
```
```CMD
ALTER PLUGGABLE DATABASE ALL CLOSE;
```
```CMD
SHUTDOWN IMMEDIATE;
```
```CMD
exit
```

### Commit the Container and upload to docker hub

```CMD
docker commit ORADB maximo-oracle-linux:base
```
```CMD
docker tag maximo-oracle-linux:base codersyacht/maximo-oracle-linux:base
```
```CMD
docker rmi maximo-oracle-linux:base
```
```CMD
docker images
```
```CMD
docker push codersyacht/maximo-oracle-linux:base
```
