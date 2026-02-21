## Configure slsCfg for MAS

**Prerequisite:**

SLS is already installed and running based on the successful execution of the instructions in document [SLS installation](knowledge-center/devops/maximo/operator-based-installation
/03-suite-license-service-installation.md).

The SLS has a registration key and certificate, both of which are needed for MAS to establish connection with the SLS service.

Run the below command to get the registration key of the sls service.

```CMD
oc get LicenseService sls -n ibm-sls
```

This will get output as follows:
```
NAME   VERSION   STATUS   INITIALIZED   LICENSEID      REGISTRATIONKEY                        AGE
sls    3.12.0    Ready    Initialized   10005a359c30   <Registration key value>               16h
```

Copy the registration key value. Store it in a new file named sls-registration-key under /keyfiles/. (./keyfiles/sls-registration-key). Replace if it exists.

To get the certificate run the follwoing command.

```CMD
oc describe LicenseService sls -n ibm-sls
```

In the output of the above command, look out for the following:
```YAML
Status:
  Ca:
    Secret Name:  sls-cert-ca
```

It will be sls-cert-ca. Unless it is manually changed.

Describe the secret, by running the following command.

```CMD
oc describe secret sls-cert-ca -n ibm-sls
```

In thr output of the above command, look out for the following;
```
Data
====
tls.key:  1675 bytes
ca.crt:   1359 bytes
tls.crt:  1359 bytes
```

Now, describe the ca.crt by executing the following command:

```CMD
oc get secret sls-cert-ca -n ibm-sls -o jsonpath="{.data['ca\.crt']}" | base64 -d
```

The output of the above command will display the sls certificate, in the following format.
```
-----BEGIN CERTIFICATE-----
..
-----BEGIN CERTIFICATE-----
```
You can directly copy the file by executing the following command:
```CMD
oc get secret sls-cert-ca -n ibm-sls -o jsonpath="{.data['ca\.crt']}" | base64 -d > sls.crt

```

Copy the certificate value to a new file named sls.crt under /keyfiles/. (./keyfiles/sls.crt). Replace if it exists.

At the end of the prerequisite, there should 2 files as follows under /mas-container/keyfiles directory.
- sls-registration-key
- sls.crt


**Installing slsCfg in MAS to connect to SLS Service**

Create a directory named _05-mas-slscfg_ under _mas-container_. Go into the directory.

Create a file named 01-mas-sls-registration-key.sh with the following content.
```sh
export MASREGKEY="$(<../keyfiles/sls-registration-key)"
oc create secret generic sls-registration-key --from-literal=registrationKey=${MASREGKEY} -n mas-max-core
```

Execute the following command:
```
./01-mas-sls-registration-key.sh
```
Verify if the sls-registration-key secret for MAS to connect to SLS service is created by running the following command.
```cmd
oc describe secret sls-registration-key -n mas-max-core
```

**Generate slsCfg.yaml**

slsCFg.yaml file is required to configure MAS to connect with suite license service. 

Create a new file called 02-genereteSlsCfg.sh with the following content. Otherwise go the next section _Executing MongoCfg.yaml_ to manually to constuct and execute the the file. 

```sh
#!/bin/bash

file1="
apiVersion: config.mas.ibm.com/v1
kind: SlsCfg
metadata:
  name: max-sls-system
  namespace: mas-max-core
  labels:
    mas.ibm.com/configScope: system
    mas.ibm.com/instanceId: max
spec:
  config:
    credentials:
      secretName: sls-registration-key
    url: 'https://sls.ibm-sls.maxsystem.dev.fyre.ibm.com'
  displayName: SLS (max)
  certificates:
    - alias: sls-ca
      crt: |"
file2="../keyfiles/sls.crt"
output_file="03-slsCfg.yaml"
indentation="          " # Four spaces for indentation

# Concatenate file1 as is
echo "$file1" > $output_file

# Add indentation to file2 and append to the output file
sed "s/^/$indentation/" "$file2" >> "$output_file"
```

Execute the following command:

```CMD
./02-genereteSlsCfg.sh
```

The above execution will create 03-slsCfg.yaml file

**Executing slsCfg.yaml**

The file generated in the previos step looks like this. If the  02-genereteSlsCfg.sh is not executed to generate this yaml file, then it has to be manually constructed.

```YAML
Name:         sls-registration-key
Namespace:    mas-max-core
Labels:       <none>
Annotations:  <none>

Type:  Opaque

Data
====
registrationKey:  36 bytes
[admin@maxsystem 05-mas-slscfg]$ cat 03-slsCfg.yaml 

apiVersion: config.mas.ibm.com/v1
kind: SlsCfg
metadata:
  name: max-sls-system
  namespace: mas-max-core
  labels:
    mas.ibm.com/configScope: system
    mas.ibm.com/instanceId: max
spec:
  config:
    credentials:
      secretName: sls-registration-key
    url: 'https://sls.ibm-sls.maxsystem.dev.fyre.ibm.com'
  displayName: SLS (max)
  certificates:
    - alias: sls-ca
      crt: |
          -----BEGIN CERTIFICATE-----
          MIIDvTCCAqWgAwIBAgIRAN9FwQ4S3mQvu3xUhJ9rX/kwDQYJKoZIhvcNAQELBQAw
          eDELMAkGA1UEBhMCR0IxDzANBgNVBAcTBkxvbmRvbjEPMA0GA1UECRMGTG9uZG9u
          MS0wKwYDVQQLEyRJQk0gU3VpdGUgTGljZW5zZSBTZXJ2aWNlIChJbnRlcm5hbCkx
          GDAWBgNVBAMTD3Nscy5zbHMuaWJtLmNvbTAeFw0yNTA3MDQxMjU4NTVaFw00NTA2
          MjkxMjU4NTVaMHgxCzAJBgNVBAYTAkdCMQ8wDQYDVQQHEwZMb25kb24xDzANBgNV
          BAkTBkxvbmRvbjEtMCsGA1UECxMkSUJNIFN1aXRlIExpY2Vuc2UgU2VydmljZSAo
          SW50ZXJuYWwpMRgwFgYDVQQDEw9zbHMuc2xzLmlibS5jb20wggEiMA0GCSqGSIb3
          DQEBAQUAA4IBDwAwggEKAoIBAQC3MijiOcEb/hZNSTmIqqy7iZsy5gV9uUTFfMoD
          magqX6oi6d1TqS4epD9qySfWGfPh2cLEPSXQ21Yg5RECwrDPCy8RHQmswS7/LsvJ
          g4tey/YR219w7MeL2SRaIXybcjnKhGU7+bS+e9LAe7VhpBdGlKb2zUNzeeGLzyuT
          akJMSsaSX8e8EaLWIjUWqyZwlxpXtb0WYI8sLrhStqNKi8nlietRKWkld51by0J7
          GGInFP1HkJ4JqjfoQhFZwpaMu37KrhS/RTPsU0fu/xtSOt3rB7Fuup7ppMGVejht
          bfBpYrwgWceqC47rCcQAz0wvZ43RZQt+VdV1VOkfniuowEwtAgMBAAGjQjBAMA4G
          A1UdDwEB/wQEAwICBDAPBgNVHRMBAf8EBTADAQH/MB0GA1UdDgQWBBRAPGufoU5F
          inCxZInzmcRuPmbwKDANBgkqhkiG9w0BAQsFAAOCAQEAkrxn4sbYjOVcSBjJLfn+
          QPNceKHU3U8LjdkpEpfpS1GEU4HmPPcyMJJozpnjuwjFNjH9EjX1pB2PKOSaPMs3
          FosftbHEim+KzwdwbTet9DFBhdjoHI/cHqM+3VdAav0+pwXWKQfAm1Xs0fIr6GKW
          MsWQ3lP+0/JngRXp07aYhe3HGRd4pr7kJdveQM/EFjrCutv0J46RgCjEOJBTbbth
          INUSOa8VBmgVwV6sKxaEfHCSjy81y4G3N4v3fYTGNcgD59b0Q8L9sS6LkcdNxZxZ
          kMGHpzLWDbyR29QvPvYYYBJH+Idelzzma6+RXrdqV29i5SRBLhxCwziQ6PfggK6a
          kw==
          -----END CERTIFICATE-----
```

Execute the following command:
```CMD
oc apply -f 03-slsCfg.yaml
```

Installation can take upto more than an hour depending on the hardware resources.

Execute the following command to check if the slsCfg is created successfully.

```
oc describe SlsCfg max-sls-system -n  mas-max-core
```
