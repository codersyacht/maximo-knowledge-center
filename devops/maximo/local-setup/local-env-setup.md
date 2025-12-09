
## Manual Setup of Maximo Application Suite

**Prerequisite**

[Change System Time](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/system/system-date.md)

[Create admin user](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/system/02-Linux-User-Creation.md)

[DB2 Configuration](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/db2/configuration.md)

[Java Setup](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/java/java-install.md)

[Java Path](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/java/java-path.md)

**Initial Setup**

The Maximo application need to be copied to _/home/admin/apps_. The present-working-directory should be in the following directory structure _/home/admin/apps/SMP_

```
cd /home/admin/apps
```
```CMD
eval $(crc oc-env)
```
```CMD
oc cp -n mas-max-manage max-max-manage-maxinst-5869bc54f7-lr4dd:/opt/IBM/SMP SMP
```

Set the permission of the SMP.
```cmd
cd /home/admin/apps
```
```cmd
chmod 775 -R SMP
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

**Update DB Properties**

Navigate to _/home/admin/apps/SMP/maximo/applications/maximo/properties_

Update _maximo.properties_ with the following content.

```PROP
mxe.name=MXServer
mxe.db.url=jdbc:db2://9.30.192.168:50000/MAXIMO
mxe.db.driver=com.ibm.db2.jcc.DB2Driver
mxe.db.user=db2inst1
mxe.db.password=LabMachine4@Training
mxe.db.schemaowner=MAXIMO
mxe.db.DB2sslConnection=false
```

**Generate DB Data**

Navigate to _/home/admin/apps/SMP/maximo/tools/maximo_

Execute the following command:

In live mode:

```CMD
./maxinst.sh -sMAXINDEX -tMAXDATA
```
In backendmode:

```CMD
nohup ./maxinst.sh -sMAXINDEX -tMAXDATA > maxinst.log &
```

Navigate to _/home/admin/apps/SMP/maximo/tools/maximo/log_ directory and monitor the log _Maxinst<Timestamp>.log_.


