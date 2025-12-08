## Install and Configure MongoDB

### Author: Jawahar

### Agenda

- MongoDB installation.
- Ensuring MongoDB is accessible in the network.

### Prerequisite

- Create a new user called mongo. 
- Note: In the instruction that follows, user is created with name _admin_. Replace admin user with mongo during the user creation process. Follow the instruction [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/system/user-management.md).
- Type hostname command and use the hostname in all the instruction marked as &lt;host&gt;.
```CMD
hostname
```

### MongoDB Installation

Login as mongo user.

```CMD
sudo vi /etc/yum.repos.d/mongodb-org-8.0.repo
```

```YUM
[mongodb-org-8.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/8.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://pgp.mongodb.com/server-8.0.asc
```

```CMD
sudo yum update
```

```
sudo yum install -y mongodb-org
```

### Configuring Network

```CMD
sudo vi /etc/mongod.conf
```

Modify bindIp value to **bindIp: 0.0.0.0**


### Enabling TLS

Enabliing TLS for secure connection. This is a **mandatory** step for Maximo connection

- In the instruction that follows, tls certificate is created to enable tls for mongodb server.
- Follow the instruction [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/mongo/ssl.md)

### Start MongoDB

```CMD
sudo systemctl start mongod
```

```
sudo systemctl status mongod
```

### Create MongoDB User (Optional)

Enabling admin user for MongoDB connectivity. This ia a **mandatory** step for Maximo connection.

Follow the instruction [here](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/mongo/Mongo-User-Creation.md)

### Stop MongoDB

```CMD
sudo systemctl stop mongod
```

### Checking MongoDB Logs

```
tail /var/log/mongodb/mongod.log
```

Restart mongodb service.
```CMD
sudo systemctl restart mongod
```

**Connecting to MongoDB**

Without TLS:

```CMD
mongosh --host <host> admin
```

With TLS:
```CMD
mongosh --tls --host <host> --port 27017 --tlsCAFile /etc/ssl/mongo/mongodb-cert.crt admin
```

### Result

- Installed MonggoDB
- Can connect to MongoDB server within the network
