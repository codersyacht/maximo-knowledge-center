# Create Item Set

### Author: Mohamed Jawahar Hussain

## Prerequisite:
No prerequisite required,

## Introduction

Item Sets are collections of item master records—like parts, materials, tools, and services—that can be shared among different organizations in Maximo.

```mermaid
graph LR
A[Begin] -->B[ Choose Set Type as Item]
B --> C[Create Item Set]
C --> E[End]
```

## Create Item Set

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets |
| Method | POST  |
| Payload | [here](/maximo/inventory/api/create-item-payload.json) |


## Success Criteria

- API executed successfully.
- Item Set named Devices created.

Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for Devices. If the API is successfully executed, the device set will be visible,


## Get Sets Query

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets?oslc.where=setid="CDYISET" |
| Method | GET  |
| Response | [here](/maximo/inventory/api/get-item-response.json) |

## Get Set
```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets/_Q0RZSVNFVA--
```

Result:
```JSON
{
    "spi:settype_description": "Item Sets",
    "spi:setid": "CDYISET",
    "spi:description": "CDYISET",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:setsid": 10,
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets/_Q0RZSVNFVA--",
    "spi:langcode": "EN",
    "spi:enterdate": "2026-03-06T04:29:38+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "2680652",
    "spi:hasld": false,
    "spi:settype": "ITEM",
    "spi:autoupdate": false
}
```
