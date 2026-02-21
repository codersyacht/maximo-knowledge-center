## Configure MongoCfg For MAS

**Prerequisite:**

Ensure to copy the mongoDB certificate to a new file named mongo.crt under /keyfiles/. (./keyfiles/mongo.crt). Replace if it exists.
Get the MongoDB user name and password.

**Configure MongoDB Secret.**

Create file named 01-ibm-mas-mongo-credentials.sh with the following content.
```
oc create secret generic ibm-mas-mongo-credentials --from-literal=username=admin  --from-literal=password=password -n mas-max-core
```

Execute the following command:
```CMD
./01-ibm-mas-mongo-credentials.sh
```
This will create the mongo secret named ibm-mas-mongo-credentials.

Verify the same.

```cmd
oc describe secret ibm-mas-mongo-credentials -n mas-max-core
```

**Generate MongoCfg.yaml**

MongoCfg.yaml file is required to configure MAS to connect with MongoDB. 

Create a new file called 02-generateMongoCfg.sh with the following content. Otherwise go the next section _Executing MongoCfg.yaml_ to manually to constuct and execute the the file. 

```sh
#!/bin/bash

file1="
apiVersion: config.mas.ibm.com/v1
kind: MongoCfg
metadata:
  name: max-mongo-system
  namespace: mas-max-core
  labels:
    mas.ibm.com/configScope: system
    mas.ibm.com/instanceId: max
spec:
  config:
    credentials:
      secretName: ibm-mas-mongo-credentials
    hosts:
      - host: maxsystem.dev.fyre.ibm.com
        port: 27017
    authMechanism: DEFAULT
    configDb: admin
    retryWrites: true
    tlsInsecure: false
  displayName: MongoDb
  certificates:
    - alias: mongodb
      crt: |"

file2="../keyfiles/mongo.crt"
output_file="03-MongoCfg.yaml"
indentation="          " # Four spaces for indentation

# Concatenate file1 as is
echo "$file1" > $output_file

# Add indentation to file2 and append to the output file
sed "s/^/$indentation/" "$file2" >> "$output_file"
```

Execute the following command:

```CMD
./02-generateMongoCfg.sh
```

The above execution will create 03-MongoCfg.yaml file

**Executing MongoCfg.yaml**

The file generated in the previos step looks like this. If the 02-generateMongoCfg.sh is not executed to generate this yaml file, then it has to be manually constructed.

```yaml
kind: MongoCfg
metadata:
  name: max-mongo-system
  namespace: mas-max-core
  labels:
    mas.ibm.com/configScope: system
    mas.ibm.com/instanceId: max
spec:
  config:
    credentials:
      secretName: ibm-mas-mongo-credentials
    hosts:
      - host: maxsystem.dev.fyre.ibm.com
        port: 27017
    authMechanism: DEFAULT
    configDb: admin
    retryWrites: true
    tlsInsecure: false
  displayName: MongoDb
  certificates:
    - alias: mongodb
      crt: |
          -----BEGIN CERTIFICATE-----
          MIIEDTCCAvWgAwIBAgIUbhJdSUi9/+J+tb3iSzjw1njRAkMwDQYJKoZIhvcNAQEL
          BQAwgZUxCzAJBgNVBAYTAklOMQswCQYDVQQIDAJLQTELMAkGA1UEBwwCQkwxETAP
          BgNVBAoMCFBlcnNvbmFsMREwDwYDVQQLDAhQZXJzb25hbDEhMB8GCSqGSIb3DQEJ
          ARYSbWQuamF3YWhhckBpYm0uY29tMSMwIQYDVQQDDBptYXhzeXN0ZW0uZGV2LmZ5
          cmUuaWJtLmNvbTAeFw0yNTA2MTgxNDAyNDNaFw0zNTA2MTYxNDAyNDNaMIGVMQsw
          CQYDVQQGEwJJTjELMAkGA1UECAwCS0ExCzAJBgNVBAcMAkJMMREwDwYDVQQKDAhQ
          ZXJzb25hbDERMA8GA1UECwwIUGVyc29uYWwxITAfBgkqhkiG9w0BCQEWEm1kLmph
          d2FoYXJAaWJtLmNvbTEjMCEGA1UEAwwabWF4c3lzdGVtLmRldi5meXJlLmlibS5j
          b20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCyQIjBCsJ7s3Z49lS5
          PMumkHbd6UBOeM0Qd1/67pWdKW3xQcffYO++wvpkFdJzxtsq3gKycv6VVQeNDW+a
          8VmskvEp4mzZTSQAkdtGXgs+z7FbE/22Ok+U7R14EtLzdLi+Uyo13sV/45In1Hb9
          IMPddB2kSJu+RvQGXZehVHdrS5e6SLdrN3bq6nFZxdzgeSKcdi5sd7EJO1wYOZbY
          OVXZQmuXe7wzj0p8vmwgT8na9AlpkmsypsGsP/EC94XXOf7VOeUAE5H3+lMTmJ2M
          88cQeJcf+awr7jINvICjkx8I/TNWlnLbNV0wSsz3KJF6jXf5W8c//H5SC93fGwlH
          s9SpAgMBAAGjUzBRMB0GA1UdDgQWBBTFl8vbDU/qQ1SLXT6CI9XswbPMyDAfBgNV
          HSMEGDAWgBTFl8vbDU/qQ1SLXT6CI9XswbPMyDAPBgNVHRMBAf8EBTADAQH/MA0G
          CSqGSIb3DQEBCwUAA4IBAQCR3C5Dn1iqhC+49sU5SUEC2zIJKftTSMYYTkopIrek
          dun5+wS4l4QjD0zkdNTZlxzcoi/zgJgMudTnJMEyQE79hC4IrYQ4GFNV+my+dpHW
          hiZm9hOegZn9OtloxDRdGuThzpSA4d3R8VZPKz4/6ntr6KlGbsTK0PcETYNdpog1
          wsnqDHnkhnXJxfSZZ270QViR1iNCQzD6GvBPKiQcD7DDt1Vs1zi5VsXnD/bfMWJg
          AYi58hR1ZlzVFd+o0c1wo6RfNeAZe0jSyU7UVnnwjkOVbZrcqn+sWoWnb/4VewVc
          3vgPolGYGa0C3aZ+NeofL5JXvkQEx36vvtCfHij5mwis
          -----END CERTIFICATE-----
```

Execute the following command:
```CMD
oc apply -f 03-MongoCfg.yaml
```
