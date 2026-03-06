# Create Item Set

### Author: Mohamed Jawahar Hussain

### Prerequisite:
Manage application installed and running.

## Introduction

Item Sets are collections of item master records—like parts, materials, tools, and services—that can be shared among different organizations in Maximo.


## Create Item Set

URL: http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets
Method: Post
Body:
```JSON
{
    "spi:settype_description": "CDYISET",
    "spi:setid": "CDYISET",
    "spi:description": "CDYISET",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:langcode": "EN",
    "spi:enterby": "MAXADMIN",
    "spi:settype": "ITEM"

}
```

## Success Criteria

- API executed successfully.
- Item Set named Devices created.

Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for Devices. If the API is successfully executed, the device set will be visible,


## Get Sets Query

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?oslc.where=setid="CDYISET"
```

Result:
```JSON
{
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "oslc:responseInfo": {
        "rdf:about": "http://localhost/maximo/oslc/os/mxapisets?oslc.where=setid=%22CDYISET%22"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_Q0RZSVNFVA--"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets"
}
```

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
