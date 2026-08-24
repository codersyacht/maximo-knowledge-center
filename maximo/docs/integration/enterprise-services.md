# Enterprise Service

### Author: Mohamed Jawahar Hussain

## Introduction

Enterprise Service are used to consume messages from the inbound queue and perform action on them. 

## Prerequisite

## Prerequisite

Configure external system. In this example, a custom queue that resides within the internal JMS server is used for demonstration purpose.
|Action|Reference|
|------|---------|
|JMS Server|[here](/devops/liberty/jms/configuration.md)|
|JMS Client|[here](/devops/liberty/jms/configuration.md)|

## Process Diagram

```mermaid
graph LR
A[Define Enterprise Service] --> B[Select Operation]
B --> C[Select MXITEM]
C --> D[Save]
```

## Execution Steps

- Navigate to Integration --> Enterprise Services. Select New Enterprise Services.
- Provide The following values:

|Attribute|Value|
|---|----|
|Enterprise Service|consumer|
|Operation|Sync|
|Object Structure|MXITEM|

- Save.
