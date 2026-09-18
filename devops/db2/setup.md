# DB2 Setup

**1. Download the relevant version of DB2.**

In this setup the version used is **DB2 Server v12.1.5.0** <br>

**2. Download the installables to the machine where it needs to be installed.**

Login to the machine where DB2 need to be installed as **root** user.

On the host machine create a directory /root/installables/db2.
```CMD
mkdir -p /root/installables/db2
```
```CMD
cd /root/installables/db2
```
Download the DB2 Server v12.1.5

[https://www.ibm.com/support/pages/db2-version-121-mod-5-fix-pack-0-linux-unix-and-windows](https://www.ibm.com/support/fixcentral/swg/selectFixes?parent=ibm%7EInformation%20Management&product=ibm/Information+Management/DB2&release=All&platform=Linux+64-bit,x86_64&function=all)

Select the latest DB2 Server Fix Pack. In this example DB2-linuxx64-server_dec-12.1.5.0-FP000 is used. Download and save the compressed file as DB2_Svr_12.1.5_linuxx64.tar.gz in /root/installables/db2.

**3. DB2 installation.**

Login in to the remote machine using root. 

Extract the compressed file and begin installation.

```CMD
tar -xvf DB2_Svr_12.1.5_linuxx64..tar.gz
```
```CMD
cd server_dec/
```
Create a file called db2server.rsp. Sample file is available in the following link. Modify as required. <br>
[DB2 response file](/devops/db2/artifacts/db2server.rsp)

```CMD
yum install -y libxcrypt-compat
```

```CMD
./db2setup -r /root/installables/db2/server_dec/db2server.rsp -f sysreq
```
If successfully installed the following message will appear.

```TXT
DBI1191I  db2setup is installing and configuring DB2 according to the
      response file provided. Please wait.
The execution completed with warnings.
For more information see the DB2 installation log at "/tmp/db2setup.log".
[root@machine1 server_dec]#
```
Check the mentioned log for more details.

You should see the following:

```TXT
Initializing instance list :.......Success 
The instance "db2inst1" has been created successfully.

The value "SVCENAME=db2c_db2inst1" was set in the DBM CFG file for the
"db2inst1" instance.

The value "DB2AUTOSTART=YES" was set in the Profile Registry for the "db2inst1"
instance.

Configuring DB2 instances :.......Success 
Registering DB2 Update Service :.......Success 
Updating global profile registry :.......Success
```

**Logging in as db2inst1**

If the db2server.rsp was used without any modification, the default DB2 user name is _db2inst1_ and the password is _Db2UnbreakableV12Engine_.

Login to the machine as db2inst1

**Check version**

```CMD
db2level
```
