## Mongo User Creation

**Connect to admin db**

Without TLS:
```CMD
mongosh --host <host> --port 27017 admin
```
With TLS:
```CMD
mongosh --tls --host <host> --port 27017 --tlsCAFile mongodb-cert.crt admin
```

**Create mongodb user**

```JSON
db.createUser
(
    { user: "admin", pwd: "password", 
    roles: 
    [ 
        { role: "userAdminAnyDatabase", db: "admin" },
        { role: "readWriteAnyDatabase", db: "admin" },
        { role: "dbAdminAnyDatabase", db: "admin" }
    ]
    }
)
```

**Connecting with credentials**

Without TLS:
```CMD
mongosh --host <host> --port 27017  -u "admin" -p "password" admin
```
With TLS:
```CMD
mongosh --tls --host <host> --port 27017 --tlsCAFile /etc/ssl/mongo/mongodb-cert.crt --authenticationDatabase "admin" -u "admin" -p "password" admin
```

**Connecting with credentials to be different db**

mongosh --port 27017 --authenticationDatabase "admin"  -u "admin" -p "password" max


**Create collection**

```cmd
db.user.insert({name: "Jawahar Hussain", age: 42})
```
