## Configure JdbcCfg For MAS

### Prerequisite:

- Get the DB2 user name and password.
- Get the DB2 URL.

### Create Secret for JDBC Connection

Create a directory named _07-mas-jdbccfg_ under _mas-container_. Go to the folder.

Create a file named 01-ibm-mas-jdbc-credentials.sh with the following content. Replace the user name and password accordibgly:

```
oc create secret generic ibm-mas-jdbc-credentials --from-literal=username=db2inst1  --from-literal=password=LabMachine4@Training -n mas-max-core
```

Execute the following command:
```CMD
./01-ibm-mas-jdbc-credentials.sh
```

Verify the secret:
```CMD
oc get secret ibm-mas-jdbc-credentials -n mas-max-core
```

Create a new file named 02-JdbcCfg.yaml with the following content. Ensure to change the URL as per the server details. 

```YAML
apiVersion: config.mas.ibm.com/v1
kind: JdbcCfg
metadata:
  name: max-jdbc-system
  namespace: mas-max-core
  labels:
    mas.ibm.com/applicationId: manage
    mas.ibm.com/configScope: workspace-application
    mas.ibm.com/instanceId: max
    mas.ibm.com/workspaceId: max
spec:
  config:
    credentials:
      secretName: ibm-mas-jdbc-credentials
    sslEnabled: false
    url: 'jdbc:db2://maxsystem.dev.fyre.ibm.com:50000/MAXIMO'
  displayName: Maximo Database
```

Execute the following command:
```
oc apply -f 02-JdbcCfg.yaml
```

Verify the same.
```CMD
oc describe JdbcCfg max-jdbc-system -n mas-max-core
```
