### DB2 Setup

**1. Download the relevant version of DB2.**

In this setup the version used is **DB2_Svr_11.5_Linux_x86-64.tar.gz** <br>
Download location:<br>
[DB2 Download](https://w3south-limited-use.cpc.ibm.com/software/xl/download/ticket.wss) <br>
part number: **CC1U0ML**

**2. Copy the compressed file to the machine where it need to be installed.**

Login to the machine where DB2 need to be installed as **root** user.

On the host machine create a directory /root/installables/db2.
```CMD
mkdir -p /root/installables/db2
```
```CMD
cd /root/installables/db2
```

If the DB2 installable package is available in box, the following command can be used to copy.
```CMD
wget -O DB2_Svr_11.5_Linux_x86-64.tar.gz https://ibm.box.com/shared/static/js24c9dbdf1dom2mmxfwn58m9ln4jclb.gz
```

In this example the installable **/root/installables/db2/DB2_Svr_11.5_Linux_x86-64.tar.gz**

**3. DB2 installation.**

Login in to the remote machine using root. 

explode the compressed file and begin installation.

```CMD
tar -xvf DB2_Svr_11.5_Linux_x86-64.tar.gz
```
```CMD
cd server_dec/
```
Create a file called db2server.rsp. Sample file is available in the following link. Modify as required. <br>
[DB2 response file](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/db2/artifacts/db2server.rsp)

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

If the db2server.rsp was used without any modification, the default DB2 user name is _db2inst1_ and the password is _LabMachine4@Training_.

Login to the machine as db2inst1

**Check version**

```CMD
db2level
```
