# Maximo JDBC Configuration

### Author: Jawahar

## Maximo Properties

**maximo.properties**

```PROP
##############################################################
# CORE DATABASE CONNECTION
##############################################################

mxe.name=MXServer

# SQL Server on Linux uses the same JDBC URL format
mxe.db.url=jdbc:sqlserver://9.30.87.54:1433;databaseName=Maximo;encrypt=true;trustServerCertificate=true;
mxe.db.driver=com.microsoft.sqlserver.jdbc.SQLServerDriver

mxe.db.user=sa
mxe.db.password=LabMachine4@Training
mxe.db.schemaowner=dbo

##############################################################
# SECURITY KEYS (same as your working version)
##############################################################

mxe.security.cryptox.key=jCjhgWgbHkCQCMlkvxaMiRGN
mxe.security.crypto.key=bpsTRPDksiOTOJIvDhmVxITV
mxe.security.old.cryptox.key=jCjhgWgbHkCQCMlkvxaMiRGN
mxe.security.old.crypto.key=bpsTRPDksiOTOJIvDhmVxITV

mxe.logging.CorrelationEnabled=0

##############################################################
# SQL SERVER PROPERTIES
##############################################################

mxe.db.vendor=sqlserver
mxe.db.dbproduct=sqlserver
mxe.db.server.version=2022
mxe.db.start=sqlserver

##############################################################
# FILEGROUP CONFIGURATION FOR MAXINST
# Using ONLY MAXDATA and MAXINDEX (no MAXLOBS)
##############################################################

# All table row data → MAXDATA
mxe.db.sqlserver.varchar=MAXDATA
mxe.db.sqlserver.longvarchar=MAXDATA

# LOB types also stored in MAXDATA
mxe.db.sqlserver.maxvarchar=MAXDATA
mxe.db.sqlserver.dbclob=MAXDATA
mxe.db.sqlserver.text=MAXDATA

# Indexes → MAXINDEX
mxe.db.sqlserver.index=MAXINDEX

# Optional fallback (ignored if above are present)
mxe.db.fileGroup=PRIMARY
```
