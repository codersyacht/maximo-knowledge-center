# Site

### Author: Mohamed Jawahar Hussain

### Prerequisite

Organization defined.

## Introduction

A site is a division within an organization that maintains certain data independently from other sites.”

## Create Site

| Field  | Value |
|--------|-------|
| URL    | http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization/_Q0RZ |
| Method | POST  |

```JSON
{
    "spi:site": [
        {
            "spi:description": "BL",
            "spi:changeby": "MAXADMIN",
            "spi:enterby": "MAXADMIN",
            "spi:active": false,
            "spi:contact": "MAXADMIN",
            "spi:siteid": "BL"
        }
    ]
}
```

## Success Criteria
API executed successfully.
Site BL created.

### Get Sites 

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisite?oslc.where=siteid="BL"
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
        "rdf:about": "http://localhost/maximo/oslc/os/mxapisite?oslc.where=siteid=%22BL%22"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisite/_Qkw-"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisite"
}
```

Specific Site:

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisite/_Qkw-
```
Method: Get
Result:
```JSON
{
    "spi:siteuid": 35,
    "spi:description": "BL",
    "billtoshipto_collectionref": "http://localhost/maximo/oslc/os/mxapisite/_Qkw-/billtoshipto",
    "spi:changeby": "MAXADMIN",
    "spi:orgid": "CDY",
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisite/_Qkw-",
    "spi:enterdate": "2026-03-06T04:39:00+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "2683737",
    "spi:active": false,
    "spi:contact": "MAXADMIN",
    "spi:changedate": "2026-03-06T04:39:00+00:00",
    "spi:siteid": "BL"
}
```
