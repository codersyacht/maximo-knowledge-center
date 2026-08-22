# External System

### Author: Mohamed Jawahar Hussain

## Introduction

External System consists of configuration to interact with external system. It can be used to both publish and/or consume messages from external system.

## Prerequisite

**Publishing Message to external System**

|Action|Reference|
|-------|--------|
|Publish Channel|[here](/maximo/docs/integration/publish-channels.md)|

**Consuming Message to external System**

|Action|Reference|
|-------|--------|
|Enterprise Service|[here](/maximo/docs/integration/enterprise-services.md)|

## Process Diagram

**Publishing Message to external System**

```mermaid
graph LR
A[Define External System] --> B{Is Sequential}
B --> |Yes| C[Select Outbound Sequential Queue]
B --> |No| D[Select Outbound Continuous Queue]
C --> E[Endpoint]
D --> E
E --> F[Publish Channel & Endpoint]
F --> G[Save]
G --> H[Enable External System]
H --> I[Enable Publish Channel]
```


