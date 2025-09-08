## Item Sets

### Prerequisite

Maximo installed and manage application accessible. 

### Introduction

Item Sets are collections of item master records—like parts, materials, tools, and services—that can be shared among different organizations in Maximo.

### Create Item Set

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{
    "spi:settype_description": "Item Sets",
    "spi:setid": "Devices",
    "spi:description": "Devices",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:langcode": "EN",
    "spi:enterby": "MAXADMIN",
    "spi:settype": "ITEM"

}
```

### Success Criteria
API executed successfully.
Item Set named Devices created.

### Het Sets Query

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin&oslc.where=setid="DEVICES"
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
        "rdf:about": "http://localhost/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin&oslc.where=setid=%22DEVICES%22"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_REVWSUNFUw--"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets"
}
```

### Get Sets
```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets/_REVWSUNFUw--?_lid=maxadmin&_lpwd=maxadmin
```

Result:
```JSON
{
    "spi:settype_description": "Item Sets",
    "spi:setid": "DEVICES",
    "spi:description": "Devices",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:setsid": 8,
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets/_REVWSUNFUw--",
    "spi:langcode": "EN",
    "spi:enterdate": "2025-09-08T05:20:01+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "1376471",
    "spi:hasld": false,
    "spi:settype": "ITEM",
    "spi:autoupdate": false
}
```
