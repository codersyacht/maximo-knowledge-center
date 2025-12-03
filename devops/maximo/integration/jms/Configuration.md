# IBM Liberty Server JMS Configuration

### Author: Jawahar

Prerequisite:

Feature install the folllowing on the Liberty Server.

- jaxrs-2.1
- servlet-4.0
- wasJmsServer-1.0
- wasJmsClient-2.0
- jndi-1.0
- jmsMdb-3.2
- mdb-3.2

Follow the instruction [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/admin/Feature-Installation.md) to install the above features.

Refer [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/jms/JMSConfiguration1.md) to learn more about JMS configuration in WebSphere Liberty.


### Maxinmo Speficic JMS Configuration for Liberty server.xml

```XML
<server description="manage">

    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
            <feature>wasJmsServer-1.0</feature>
            <feature>jmsMdb-3.2</feature>
            <feature>mdb-3.2</feature>
    </featureManager>

    <httpEndpoint id="defaultHttpEndpoint" host="*"  httpPort="9090" httpsPort="9453" />
    <applicationManager autoExpand="true"/>
    <wasJmsEndpoint host="*" wasJmsSSLPort="7286" wasJmsPort="7276" />

    <messagingEngine>
        <fileStore path="/jmsstore" fileStoreSize="4096" logFileSize="1024"/>
        <queue id="sqoutbd" maintainStrictOrder="true" maxMessageDepth="100000"
        failedDeliveryPolicy="KEEP_TRYING" maxRedeliveryCount="-1"/>
        <queue id="sqinbd" maintainStrictOrder="true" maxMessageDepth="200000"
        failedDeliveryPolicy="KEEP_TRYING" maxRedeliveryCount="-1"/>
        <queue id="cqinerrbd" maxMessageDepth="100000" exceptionDestination="cqinerrbd"/>
        <queue id="cqinbd" maxMessageDepth="100000" exceptionDestination="cqinerrbd"/>
        <queue id="cqouterrbd" maxMessageDepth="100000" exceptionDestination="cqouterrbd"/>
        <queue id="cqoutbd" maxMessageDepth="100000" exceptionDestination="cqouterrbd"/>
        <queue id="notferrbd" maxMessageDepth="100000" exceptionDestination="notferrbd"/>
        <queue id="notfbd" maxMessageDepth="100000" exceptionDestination="notferrbd"/>
    </messagingEngine>

</server>
```
