## MongoDB Operations

**Note:**
admin, config and local are default daatabases.

**Login to MongoDB**

[Login](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/mongo/Mongo-User-Creation.md) <br>
[Secured Login](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/mongo/Mongo-Enable-SSL-TLS.md)


**List DB**
```CMD
show databases;
```

**Create DB**

```CMD
use <databaseName>
```

**List collections**
```CMD
show collections;
```

**Delete Collection**
```CMD
db.<collection-name>.drop()
```
**Delete DB**
```CMD
use <databaseName>
```
```CMD
db.dropDatabase()
```
