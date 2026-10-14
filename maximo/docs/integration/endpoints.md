# Endpoints

### Author: Mohamed Jawahar Hussain

## Introduction

The endpoint is a protocol based configuration using which a publish channel will post maximo message to an external system.

## Prerequisite

Configure external system. In this example, a custom queue that resides within the internal JMS server is used for demonstration purpose.
|Action|Reference|
|------|---------|
|JMS Server|[here](/devops/liberty/jms/configuration.md)|
|JMS Client|[here](/devops/liberty/jms/configuration.md)|

## Process Diagram

Not Applicable.

## Execution Steps

Navigate to Endpoints and select New endpoint.

|Attribute|Value|
|------|---------|
|Endpoint Name|publish|
|Description|publish|
|Handler|JMS|
|Consumed By|Integration|
|DESTINATIONTYPE|queue|
|ISTEXT|1|
|DESTJNDINAME|jms/maximo/int/queues/external|
|CONFACTORYJNDINAME|jms/maximo/int/cf/intcf|

Click Test and provice the following in the Test Data section:

```XML
<?xml version="1.0" encoding="UTF-8"?>
<test>hello</test>
```

## Success Metric

Test should return the following:
```
BMXAA1241I - The end point test was successful for end point PUBLISH.
```

Publish Channel successfully defined.

## Next Step

|Action|Reference|
|------|---------|
|Configure Publish Channel|[here](/maximo/docs/integration/publish-channels.md)|
