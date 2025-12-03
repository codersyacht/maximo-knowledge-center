## IBM Liberty Server JMS Configuration

### Author: Jawahar

**Liberty server.xml **

Most basic element for configuring JMS server in Liberty is as follows. This is generic and it is not the required configuration for Maximo.

```JMS
<server description="new server">
    <!-- Enable features -->
    <featureManager>
            <feature>webProfile-8.0</feature>
            <feature>jaxrs-2.1</feature>
            <feature>servlet-4.0</feature>
<feature>wasJmsServer-1.0</feature>
    </featureManager>

    <!-- To access this server from a remote client add a host attribute to the following element, e.g. host="*" -->
    <httpEndpoint id="defaultHttpEndpoint" host="*"
                  httpPort="9090"
                  httpsPort="9453" />

    <!-- Automatically expand WAR files and EAR files -->
    <applicationManager autoExpand="true"/>

    <messagingEngine>
        <fileStore path="/home/admin/apps/wlp/usr/servers/jmsserver/jmsstore"/>
        <queue id="QUEUE1"/>
    </messagingEngine>

    <wasJmsEndpoint host="*" wasJmsPort="9011" wasJmsSSLPort="9100" />
 </server>
```
