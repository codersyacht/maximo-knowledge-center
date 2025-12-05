# Maximo Deployment

### Author: Jawahar

## Prerequisite

**Liberty Setup**

[Liberty Installation](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/admin/install.md)

Following the instructions [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/admin/Feature-Installation.md) and install the following features.

- javaMail-1.6
- jdbc-4.2
- installFeature jaxws-2.2
- installFeature servlet-4.0
- installFeature jndi-1.0
- wasJmsServer-1.0
- wasJmsClient-2.0
- wmqJmsClient-2.0
- ssl-1.0
- jmsMdb-3.2
- openidConnectClient-1.0
- ejbRemote-3.2
- ejbHome-3.2
- jsonp-1.1
- springBoot-3.0


**Deploy the Application**

[Deployment](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/liberty/03-Maximo-Deployment.md)

**Start the Server**

[Start Server](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/liberty/04-Server-Start-Stop.md)


Access the application.

_http://9.30.192.168:9080/maximo_

username: maxadmin
password: maxadmin
