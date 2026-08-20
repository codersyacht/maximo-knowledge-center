

```CMD
openssl req -newkey rsa:2048 -new -x509 -days 3650 -nodes -subj '/C=IN/ST=KA/L=BL/O=Personal/OU=Personal/emailAddress=md.jawahar@ibm.com/CN=localhost' -out liberty.crt -keyout liberty.key
```

```CMD
openssl pkcs12 -export -in liberty.crt  -inkey liberty.key -out liberty.p12 -name default -passout pass:password
```

```CMD
keytool -list -v -keystore liberty.p12 -storetype PKCS12
```
