# Liberty Server JMS Configuration

### Author: Jawahar


**Prerequisite:**

Feature install the folllowing on the Liberty Server.

- jaxrs-2.1
- servlet-4.0
- wasJmsServer-1.0
- wasJmsClient-2.0
- jndi-1.0
- jmsMdb-3.2
- mdb-3.2

 Follow the instruction [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/admin/Feature-Installation.md) to install the above features. 



## Generic JMS Configuration for Liberty server.xml

Most basic element for configuring JMS server in Liberty is as follows. This is generic and it is not the required configuration for Maximo.

```XML
<server description="jmsserver">

    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
            <feature>wasJmsServer-1.0</feature>
             <feature>wasJmsSecurity-1.0</feature>
    </featureManager>

    <httpEndpoint id="defaultHttpEndpoint" host="*"  httpPort="9090" httpsPort="9453" />
    <applicationManager autoExpand="true"/>
    <wasJmsEndpoint host="*" wasJmsSSLPort="7286" wasJmsPort="7276" />

    <messagingEngine>
        <fileStore path="/home/admin/apps/wlp/usr/servers/jmsserver/jmsstore" fileStoreSize="4096" logFileSize="1024"/>
        <queue id="sqoutbd" maintainStrictOrder="true" maxMessageDepth="100000" failedDeliveryPolicy="KEEP_TRYING" maxRedeliveryCount="-1"/>
        <queue id="sqinbd" maintainStrictOrder="true" maxMessageDepth="200000" failedDeliveryPolicy="KEEP_TRYING" maxRedeliveryCount="-1"/>
        <queue id="cqinerrbd" maxMessageDepth="100000" exceptionDestination="cqinerrbd"/>
        <queue id="cqinbd" maxMessageDepth="100000" exceptionDestination="cqinerrbd"/>
        <queue id="cqouterrbd" maxMessageDepth="100000" exceptionDestination="cqouterrbd"/>
        <queue id="cqoutbd" maxMessageDepth="100000" exceptionDestination="cqouterrbd"/>
        <queue id="notferrbd" maxMessageDepth="100000" exceptionDestination="notferrbd"/>
        <queue id="notfbd" maxMessageDepth="100000" exceptionDestination="notferrbd"/>
    </messagingEngine>

 </server>
```

```XML
<server description="new server">

    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
            <feature>wasJmsServer-1.0</feature>
            <feature>wasJmsClient-2.0</feature>
            <feature>jndi-1.0/feature>
            <feature>jmsMdb-3.2</feature>
            <feature>mdb-3.2</feature>
    </featureManager>

    <httpEndpoint id="defaultHttpEndpoint" host="*"  httpPort="9090" httpsPort="9453" />
    <applicationManager autoExpand="true"/>
    <wasJmsEndpoint host="*" wasJmsSSLPort="7286" wasJmsPort="7276" />

    <jmsQueueConnectionFactory jndiName="jms/maximo/int/cf/intcf" connectionManagerRef="mifjmsconfact">
          <properties.wasJms remoteServerAddress="codehub1.fyre.ibm.com:7276:BootstrapBasicMessaging"/></jmsQueueConnectionFactory>
    <connectionManager id="mifjmsconfact" maxPoolSize="20"/>

    <jmsQueue jndiName="jms/maximo/int/queues/sqout"><properties.wasJms queueName="sqoutbd"/></jmsQueue>
    <jmsQueue jndiName="jms/maximo/int/queues/sqin"><properties.wasJms queueName="sqinbd"/></jmsQueue>
    <jmsQueue jndiName="jms/maximo/int/queues/cqin"><properties.wasJms queueName="cqinbd"/></jmsQueue>
    <jmsQueue jndiName="jms/maximo/int/queues/cqinerr"><properties.wasJms queueName="cqinerrbd"/></jmsQueue>
    <jmsQueue jndiName="jms/maximo/int/queues/cqout"><properties.wasJms queueName="cqoutbd"/></jmsQueue>
    <jmsQueue jndiName="jms/maximo/int/queues/cqouterr"><properties.wasJms queueName="cqouterrbd"/></jmsQueue>
    <jmsQueue jndiName="jms/maximo/int/queues/notf"><properties.wasJms queueName="notfbd"/></jmsQueue>
    <jmsQueue jndiName="jms/maximo/int/queues/notferr"><properties.wasJms queueName="notferrbd"/></jmsQueue>


    <jmsActivationSpec id="maximo-all/mboejb/JMSContQueueProcessor-1" maxEndpoints="5"><properties.wasJms destinationLookup="jms/maximo/int/queues/cqin"
    maxConcurrency="5" maxBatchSize="20" connectionFactoryLookup="jms/maximo/int/cf/intcf"/></jmsActivationSpec>
    <jmsActivationSpec id="maximo-all/mboejb/JMSContQueueProcessor-2" maxEndpoints="1"><properties.wasJms destinationLookup="jms/maximo/int/queues/cqinerr"
    maxConcurrency="1" maxBatchSize="20" connectionFactoryLookup="jms/maximo/int/cf/intcf"/></jmsActivationSpec>
    <jmsActivationSpec id="maximo-all/mboejb/JMSContOutQueueProcessor-1" maxEndpoints="5"><properties.wasJms destinationLookup="jms/maximo/int/queues/cqout"
    maxConcurrency="5" maxBatchSize="20" connectionFactoryLookup="jms/maximo/int/cf/intcf"/></jmsActivationSpec>
    <jmsActivationSpec id="maximo-all/mboejb/JMSContOutQueueProcessor-2" maxEndpoints="1"><properties.wasJms destinationLookup="jms/maximo/int/queues/cqouterr"
    maxConcurrency="1" maxBatchSize="20" connectionFactoryLookup="jms/maximo/int/cf/intcf"/></jmsActivationSpec>
</server>

 </server>
```




    

   
