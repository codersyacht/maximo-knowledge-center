
## Enable SSL/TLS for MongoDB

### Author: Jawahar

### Prerequisite

- Type hostname command and use the hostname in all the instruction marked as &lt;host&gt;.
  
```CMD
hostname
```

Stop MongoDB if it is running.
```CMD
sudo systemctl stop mongod
```

### Create Certificates

Create Certificates in /etc/ssl/mongo directory.
```CMD
cd /etc/ssl/
```
```CMD
sudo mkdir mongo
```
```CMD
sudo chmod 775 -R mongo
```
```
cd mongo
```

Follow the instructuon [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/system/ssl-setup.md) to create the certificate.

**Edit /etc/mongod.conf, network interfaces section**

```CMD
sudo vi /etc/mongod.conf
```

```YAML
# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0  # Enter 0.0.0.0,:: to bind to all IPv4 and IPv6 addresses or, alternatively, use the net.bindIpAll setting.
  tls:
    mode: requireTLS
    certificateKeyFile: /etc/ssl/mongo/mongodb.pem
    CAFile: /etc/ssl/mongo/mongodb-cert.crt
    allowConnectionsWithoutCertificates: true
    allowInvalidCertificates: true
    allowInvalidHostnames: true
```

**Restart/Start mongo**
```CMD
sudo systemctl start mongod
```

If there are any issues check the log at /var/log/mongodb/mongod.log.

**Test the connection**

without authentication.

```CMD
mongosh --host <host> --tls --tlsCAFile /etc/ssl/mongo/mongodb-cert.crt admin
``` 
with authentication:

```CMD
mongosh --tls --host <host> --port 27017 --tlsCAFile /etc/ssl/mongo/mongodb-cert.crt --authenticationDatabase "admin" -u "admin" -p "password" admin
```
