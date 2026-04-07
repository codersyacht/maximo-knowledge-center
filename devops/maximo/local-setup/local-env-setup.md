
## Manual Setup of Maximo Application Suite

**Prerequisite**

The following 2 prerequisites (Change System Time & Crete admin user) are only required if installation is made on an isolated Linux machine. Not required for Macbook installation.

- [Change System Time](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/system/system-date.md)
- [Create admin user](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/system/02-Linux-User-Creation.md)

Use either DB2 or MSSQL. If installation is on Macbook then install MSSQL only.

- [DB2 Configuration](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/db2/configuration.md)
- [MSSQL Configuration](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/mssql/setup.md)

Configure Java 
- [Java Setup](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/java/java-install.md)
- [Java Path](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/java/java-path.md)

## Initial Setup

**Linux**

The Maximo application need to be copied to _/home/admin/apps_. The present-working-directory should be in the following directory structure _/home/admin/apps/SMP_

```
cd /home/admin/apps
```

**Mac**

In this example the home directory is /Users/jawahar/codersyacht. Use an approprate location based on the environment.

**Extracting the SMP**

If SMP filesystem is readily available, it can be used. It also be copied from a remote machine. Otherwise, it can be copied from the container.

**Extracting SMP from container**

```CMD
eval $(crc oc-env)
```
```CMD
oc cp -n mas-max-manage max-max-manage-maxinst-5869bc54f7-lr4dd:/opt/IBM/SMP SMP
```

**Copying SMP from remote machine.**
```CMD
scp -o StrictHostKeyChecking=no "admin@9.30.146.6:/home/admin/apps/SMP.tar" /Users/jawahar/codersyacht/SMP.tar
```
All further steps are based on SMP folder existing in /home/admin/apps/SMP. If a different folder is used, change it accordingly.

Set the permission of the SMP.
```cmd
cd /home/admin/apps
```
```cmd
chmod -R 775 SMP
```

Content of the _/home/admin/apps/SMP/maximo_ folder.

```CMD
drwxr-xr-x 2 admin admin      6 May  6 19:12 additional-server-files
drwxr-xr-x 6 admin admin     81 May  6 19:11 applications
-rw-r--r-- 1 admin admin     30 Mar 13 14:51 build.num
-rw-r--r-- 1 admin admin    609 Mar 13 14:51 buildbase.cmd
-rwxr-xr-x 1 admin admin   2894 Mar 13 14:51 buildbase.sh
-rw-r--r-- 1 admin admin  14834 Mar 13 14:51 buildbase.xml
-rwxr-xr-x 1 admin admin    672 Mar 14 04:06 clear-session.sh
-rw-r--r-- 1 admin admin   2671 Mar 13 14:51 commonenv.xml
-rwxr-xr-x 1 admin admin   1614 Mar 14 04:06 cos.sh
drwxr-xr-x 3 admin admin   4096 Mar 14 04:12 deployment
-rw-r--r-- 1 admin admin   2638 Mar 13 14:51 devbase.xml
-rwxr-xr-x 1 admin admin   2033 Mar 14 04:06 filestorage.sh
-rwxr-xr-x 1 admin admin    655 Mar 14 04:06 functions-dbchecks.sh
-rwxr-xr-x 1 admin admin    326 Mar 14 04:06 is-maximo-db.sh
-rwxr-xr-x 1 admin admin    914 Mar 14 04:06 is-onlineupgrade-rolledback.sh
-rwxr-xr-x 1 admin admin   4440 Mar 14 04:06 is-updatedb-needed.sh
drwxr-xr-x 2 admin admin     72 May  6 19:13 lang
-rwxr-xr-x 1 admin admin   8306 May 20 06:53 maxinst.sh
-rw-r--r-- 1 admin admin     86 Mar 14 04:06 maxinst-version.yaml
-rwxr-xr-x 1 admin admin    593 Mar 14 04:06 perform-attachment.sh
-rwxr-xr-x 1 admin admin   6014 Mar 14 04:06 prepare-db.sh
-rwxr-xr-x 1 admin admin   6812 Mar 14 04:06 prepare-db-nolog.sh
-rw-r--r-- 1 admin admin 143890 Mar 13 14:51 purge.xml
-rwxr-xr-x 1 admin admin   2291 Mar 14 04:06 reencrypt.sh
drwxr-xr-x 5 admin admin     43 Mar 13 14:51 reports
drwxr-xr-x 3 admin admin     27 Mar 13 14:52 resources
-rwxr-xr-x 1 admin admin  24003 Mar 14 04:06 run-db.sh
drwxr-xr-x 3 admin admin     33 Mar 13 14:51 testcases
drwxr-xr-x 5 admin admin     43 May 22 07:31 tools
-rw-r--r-- 1 admin admin     28 Mar 13 17:56 toolsapi.build.num
-rwxr-xr-x 1 admin admin    962 Mar 14 04:06 update-masimageid.sh
-rwxr-xr-x 1 admin admin    812 Mar 14 04:06 update-masimageidfull.sh
```

### Copy Java into Maximo Runtime

Navigate to _/home/admin/apps/SMP/maximo/tools_

```CMD
cd /home/admin/apps/SMP/maximo/tools
```
```CMD
mkdir -p java/jre
```
```CMD
cd java
```

Note that the home directory for Java in Mac is /Users/jawahar/codersyacht/java/ibmjdk17/Contents/Home. The bwlow step is applicable for Linux. 
```CMD
cp -r /home/admin/apps/jdk17/* ./jre
```
For Mac
```CMD
cp -r /Users/jawahar/codersyacht/java/ibmjdk17/Contents/Home/* ./jre
```

**Set Java Path Specific For Maximo:**
```CMD
export JAVA_HOME=/home/admin/apps/SMP/maximo/tools/java/jre
```
```CMD
export PATH=$JAVA_HOME/bin:$PATH  
```


**Update DB Properties**

Navigate to _/home/admin/apps/SMP/maximo/applications/maximo/properties_

Update _maximo.properties_ with the following content.

**DB2**

```PROP
mxe.name=MXServer
mxe.db.url=jdbc:db2://9.30.192.168:50000/MAXIMO
mxe.db.driver=com.ibm.db2.jcc.DB2Driver
mxe.db.user=db2inst1
mxe.db.password=LabMachine4@Training
mxe.db.schemaowner=MAXIMO
mxe.db.DB2sslConnection=false
mxe.logging.CorrelationEnabled=0
```

**MSSQL**

Remove DB2 config
```PROP
mxe.db.url
mxe.db.driver
mxe.db.user
mxe.db.password
mxe.db.schemaowner
mxe.db.DB2sslConnection
```
Add the following and modify the values accordingly:

```PROP
mxe.db.url=jdbc:sqlserver://localhost:1433;databaseName=Maximo;encrypt=true;trustServerCertificate=true;
mxe.db.driver=com.microsoft.sqlserver.jdbc.SQLServerDriver
mxe.db.user=sa
mxe.db.password=LabMachine4@Training
mxe.db.schemaowner=dbo
mxe.db.vendor=sqlserver
mxe.db.dbproduct=sqlserver
mxe.db.server.version=2022
mxe.db.start=sqlserver
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


**Generate DB Data (optional)**

**Note:** This step is only required if DB is not populated. During container based deployment, if the tables are generated, then this step can be skipped.

Navigate to _/home/admin/apps/SMP/maximo/tools/maximo_

Execute the following command:

In live mode:

**DB2**
```CMD
./maxinst.sh -sMAXINDEX -tMAXDATA
```
**MSSQL**
```CMD
./maxinst.sh -sPRIMARY -tPRIMARY
```
In backendmode:

```CMD
nohup ./maxinst.sh -sMAXINDEX -tMAXDATA > maxinst.log &
```
or
```CMD
nohup ./maxinst.sh -sPRIMARY -tPRIMARY > maxinst.log &
```

Navigate to _/home/admin/apps/SMP/maximo/tools/maximo/log_ directory and monitor the log _Maxinst<Timestamp>.log_.


