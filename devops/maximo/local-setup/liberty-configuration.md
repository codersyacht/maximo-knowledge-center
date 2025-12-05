# Configure Liberty Server For Maximo

### Author: Jawahar

## Prerequisite
[Liberty Setup](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/liberty/01-Liberty-Setup.md)

**Install Liberty Features**

Navigate to /home/admin/apps/webprofile-8/bin.

```CMD
./featureUtility installFeature javaMail-1.6
```
```CMD
./featureUtility installFeature jdbc-4.2
```
```CMD
./featureUtility installFeature jaxws-2.2
```
```CMD
./featureUtility installFeature servlet-4.0
```
```CMD
./featureUtility installFeature jndi-1.0
```
```CMD
./featureUtility installFeature wasJmsServer-1.0
```
```CMD
./featureUtility installFeature wasJmsClient-2.0
```
```CMD
./featureUtility installFeature wmqJmsClient-2.0
```
```CMD
./featureUtility installFeature ssl-1.0
```
```CMD
./featureUtility installFeature jmsMdb-3.2
```
```CMD
./featureUtility installFeature openidConnectClient-1.0
```
```CMD
./featureUtility installFeature ejbRemote-3.2
```
```CMD
./featureUtility installFeature ejbHome-3.2
```
```CMD
./featureUtility installFeature jsonp-1.1
```
```CMD
./featureUtility installFeature springBoot-3.0
```

**JVM Properties**

Navigate to the following directory.

```CMD
cd /home/admin/apps/wlp/usr/servers/manage
```

Create a file named jvm.options with the following content.

[jvm.options](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/liberty/artifacts/jvm.options)

**Server Properties**

Navigate to the following directory

```CMD
cd /home/admin/apps/wlp/usr/servers/manage
```

Update the server.xml with the following content.

[server.xml](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/liberty/artifacts/server.xml)
