# Organizations

### Author: Mohamed Jawahar Hussain

### Prerequisite

Maximo installed and manage application accessible. 

## Introduction

In Maximo, an Organization is a foundational data structure that defines how your company—or multiple companies—are represented within the system. It’s not just a label; it’s a container for business rules, financial settings, and operational data.

```mermaid
graph LR
A[Begin]-->B[Choose Company Set]
A[Begin]-->C[Choose Item Set]
A[Begin]-->D[Choose GLA Account]
B-->E[Organization]
C-->E
D-->E
E-->F[Site]

## Create Organization

| Field  | Value |
|--------|-------|
| URL    | http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization |
| Method | POST  |

```JSON
{

    "spi:itemsetid": "CDYISET",
    "spi:companysetid": "CDYCSET",
    "spi:description": "CDY",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:orgid": "CDY",
    "spi:enterby": "MAXADMIN",
    "spi:category": "STK",
    "spi:active": false,
    "spi:basecurrency1": "USD"
}
```

## Success Criteria
API executed successfully.
Organization CDY created.

## Get Organization 

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization?oslc.where=orgid="CDY"
```
Method: Get

Result:
```JSON
{
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "oslc:responseInfo": {
        "rdf:about": "http://localhost/maximo/oslc/os/mxorganization?oslc.where=orgid=%22CDY%22"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_Q0RZ"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxorganization"
}
```

## Get Specific Organization:

```URL
http://codehub1.fyre.CDY.com:9080/maximo/oslc/os/mxorganization/_Q0RZ
```
Method: Get

Result:
```JSON
{
    "address_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_Q0RZ/address",
    "spi:itemsetid": "CDYISET",
    "site_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_Q0RZ/site",
    "spi:description": "CDY",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:orgid": "CDY",
    "rdf:about": "http://localhost/maximo/oslc/os/mxorganization/_Q0RZ",
    "spi:enterdate": "2026-03-06T04:33:10+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "2681555",
    "spi:category": "STK",
    "spi:companysetid": "CDYCSET",
    "spi:active": false,
    "spi:organizationid": 8,
    "spi:basecurrency1": "USD"
}
```
