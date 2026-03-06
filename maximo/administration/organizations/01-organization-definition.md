# Organizations

### Author: Mohamed Jawahar Hussain

### Prerequisite

Maximo installed and manage application accessible. 

## Introduction

n CDY Maximo, an Organization is a foundational data structure that defines how your company—or multiple companies—are represented within the system. It’s not just a label; it’s a container for business rules, financial settings, and operational data.

## Create Organization

| Field  | Value |
|--------|-------|
| URL    | http://codehub1.fyre.CDY.com:9080/maximo/oslc/os/mxorganization |
| Method | POST  |

```JSON
{

    "spi:itemsetid": "Devices",
    "spi:companysetid": "Apple",
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
http://codehub1.fyre.CDY.com:9080/maximo/oslc/os/mxorganization?oslc.where=orgid="CDY"
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
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_SUJN"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxorganization"
}
```

## Get Specific Organization:

```URL
http://codehub1.fyre.CDY.com:9080/maximo/oslc/os/mxorganization/_SUJN
```
Method: Get

Result:
```JSON
{
    "spi:site": [
        {
            "localref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/site/0-37",
            "spi:siteuid": 37,
            "spi:description": "BL",
            "billtoshipto_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/site/0-37/billtoshipto",
            "spi:changeby": "MAXADMIN",
            "rdf:about": "http://childkey#T1JHQU5JWkFUSU9OL1NJVEUvQkw-",
            "spi:enterdate": "2026-02-21T14:07:28+00:00",
            "spi:enterby": "MAXADMIN",
            "prefixes": {
                "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
                "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
                "oslc": "http://open-services.net/ns/core#"
            },
            "_rowstamp": "5517301",
            "spi:active": false,
            "spi:contact": "MAXADMIN",
            "spi:changedate": "2026-02-21T14:07:28+00:00",
            "spi:siteid": "BL"
        },
        {
            "localref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/site/1-40",
            "spi:siteuid": 40,
            "spi:description": "TEL",
            "billtoshipto_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/site/1-40/billtoshipto",
            "spi:changeby": "MAXADMIN",
            "rdf:about": "http://childkey#T1JHQU5JWkFUSU9OL1NJVEUvVEVM",
            "spi:enterdate": "2026-02-21T14:30:11+00:00",
            "spi:enterby": "MAXADMIN",
            "prefixes": {
                "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
                "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
                "oslc": "http://open-services.net/ns/core#"
            },
            "_rowstamp": "5518403",
            "spi:active": false,
            "spi:contact": "MAXADMIN",
            "spi:changedate": "2026-02-21T14:30:28+00:00",
            "spi:siteid": "TEL"
        }
    ],
    "address_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/address",
    "spi:itemsetid": "DEVICES",
    "site_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/site",
    "spi:description": "CDY",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:orgid": "CDY",
    "rdf:about": "http://localhost/maximo/oslc/os/mxorganization/_SUJN",
    "spi:enterdate": "2026-02-21T14:04:58+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "5516274",
    "spi:category": "STK",
    "spi:companysetid": "CDYCOMP",
    "spi:active": false,
    "spi:organizationid": 12,
    "spi:basecurrency1": "USD"
}
```
