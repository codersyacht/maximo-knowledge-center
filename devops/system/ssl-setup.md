## Create SSL/TLS Certificate

### Prerequisite

- Type hostname command and use the hostname in all the instruction marked as &lt;host&gt;.
  
```CMD
hostname
```
**Note:** Replace codehub1.fyre.ibm.com with appropriate hostname in the instruction below.

**Make PEM containig a public key certificate and its associated private key**


```CMD
sudo openssl req -newkey rsa:2048 -new -x509 -days 3650 -nodes -subj '/C=IN/ST=KA/L=BL/O=Personal/OU=Personal/emailAddress=md.jawahar@ibm.com/CN=<codehub1.fyre.ibm.com' -out mongodb-cert.crt -keyout mongodb-cert.key
```

```CMD
sudo cat mongodb-cert.key mongodb-cert.crt > mongodb.pem
```

```CMD
sudo cp mongodb-cert.crt mongodb-ca.crt
```


**Create Truststore and and certificate for accessibility from Java code**
```CMD
keytool -import -trustcacerts -keystore mongo-truststore.jks -storepass password -noprompt -file mongodb-cert.crt -alias mongodb-cert
```

### Change Owner

```CMD
sudo chmod 775 ./*
```
```CMD
sudo chown mongo:mongo ./*
```
