# Create Item Set

### Author: Mohamed Jawahar Hussain

## Introduction

Item Sets are collections of item master records—like parts, materials, tools, and services—that can be shared among different organizations in Maximo.

## Prerequisite:
No prerequisite required.

## Process Diagram

```mermaid
graph LR
A[Begin] -->B[ Choose Set Type as Item]
B --> C[Create Item Set]
C --> E[End]
```
## Execution Steps

### Create Item Set

[**API**](/maximo/api/administration/sets/api/create-item.json)


## Success Metric

- API executed successfully.
- Item Set named Devices created.

Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for Devices. If the API is successfully executed, the device set will be visible,


### Find Sets

[**API**](/maximo/api/administration/sets/api/find-item-set.json)

### Get Specific Set

[**API**](/maximo/api/administration/sets/api/get-item-set.json)

## Next Steps

|Requirement| Refecence |
|------------|-----------|
|Configure Organization|[here](/maximo/docs/administration/organizations/01-organization-definition.md)|
