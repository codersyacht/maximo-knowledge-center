## IBM Liberty Server JMS Configuration

### Author: Jawahar

#### Generic JMS Configuration for Liberty server.xml

Most basic element for configuring JMS server in Liberty is as follows. This is generic and it is not the required configuration for Maximo.

```XML
<server description="new server">
    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
            <feature>wasJmsServer-1.0</feature>
    </featureManager>
    <httpEndpoint id="defaultHttpEndpoint" host="*"  httpPort="9090" httpsPort="9453" />
    <applicationManager autoExpand="true"/>
    <wasJmsEndpoint host="*" wasJmsSSLPort="7286" wasJmsPort="7276" />
    <messagingEngine>
        <fileStore path="/home/admin/apps/wlp/usr/servers/jmsserver/jmsstore"/>
        <queue id="localqueue1"/>
        <queue id="localqueue2"/>
    </messagingEngine>
 </server>
```

If you want to use a seperate server as jms client, use the following server.xml in a new server.

```XML
<server description="new server">

    <!-- Enable features -->
    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>wasJmsClient-2.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
            <feature>jndi-1.0</feature>
    </featureManager>

    <!-- To access this server from a remote client add a host attribute to the following element, e.g. host="*" -->
    <httpEndpoint id="defaultHttpEndpoint"  httpPort="9091"  httpsPort="9454" host="*" />
                  
    <!-- Automatically expand WAR files and EAR files -->
    <applicationManager autoExpand="true"/>

    <jmsQueueConnectionFactory jndiName="jms/QCF">
       <properties.wasJms remoteServerAddress="codehub1.fyre.ibm.com:9011:BootstrapBasicMessaging"/>
    </jmsQueueConnectionFactory>

    <jmsQueue jndiName="jms/MyQueue">
       <properties.wasJms queueName="QUEUE1"/>
    </jmsQueue>

</server>
```

If you want to the server itself as the client, embed the following into the server.xxml of the jms server.

```XML
<server description="new server">
    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
            <feature>wasJmsServer-1.0</feature>
    </featureManager>
    <httpEndpoint id="defaultHttpEndpoint" host="*"  httpPort="9090" httpsPort="9453" />
    <applicationManager autoExpand="true"/>
    <wasJmsEndpoint host="*" wasJmsSSLPort="7286" wasJmsPort="7276" />
    <messagingEngine>
        <fileStore path="/home/admin/apps/wlp/usr/servers/jmsserver/jmsstore"/>
        <queue id="localqueue1"/>
        <queue id="localqueue2"/>
    </messagingEngine>

    <jmsQueueConnectionFactory jndiName="jms/QCF">
       <properties.wasJms remoteServerAddress="codehub1.fyre.ibm.com:9011:BootstrapBasicMessaging"/>
    </jmsQueueConnectionFactory>
    <jmsQueue jndiName="jms/MyQueue">
       <properties.wasJms queueName="QUEUE1"/>
    </jmsQueue>
 </server>
```
#### Maxinmo Speficic JMS Configuration for Liberty server.xml

```XML
<server description="new server">
    <!-- Enable features -->
    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
            <feature>wasJmsServer-1.0</feature>
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
