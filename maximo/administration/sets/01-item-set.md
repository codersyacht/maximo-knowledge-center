# Create Item Set

### Author: Mohamed Jawahar Hussain

## Prerequisite:
No prerequisite required,

## Introduction

Item Sets are collections of item master records—like parts, materials, tools, and services—that can be shared among different organizations in Maximo.

## Process Diagram

```mermaid
graph LR
A[Begin] -->B[ Choose Set Type as Item]
B --> C[Create Item Set]
C --> E[End]
```
## Execution Steps

### Create Item Set

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets |
| Method | POST  |
| Payload | [here](/maximo/administration/sets/api/create-item-payload.json) |


## Success Metric

- API executed successfully.
- Item Set named Devices created.

Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for Devices. If the API is successfully executed, the device set will be visible,


### Get Sets

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets?oslc.where=setid="CDYISET" |
| Method | GET  |
| Response | [here](/maximo/administration/sets/api/get-item-set-response.json) |

### Get Specific Set

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets/_Q0RZSVNFVA-- |
| Method | GET  |
| Response | [here](/maximo/administration/sets/api/get-specific-item-set-response.json) |

## Next Steps

|Requirement| Refecence |
|------------|-----------|
|Configure Organization|[here](/maximo/administration/organizations/01-organization-definition.md)|
