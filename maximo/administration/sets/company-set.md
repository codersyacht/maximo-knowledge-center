## Company Sets

### Prerequisite

Maximo installed and manage application accessible. 

### Introduction

A Company Set is a collection of company records that can be accessed by multiple organizations. This allows centralized control over vendor and business partner information, improving consistency and reducing duplication.

### Create Company Set

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{
    "spi:settype_description": "Item Sets",
    "spi:setid": "Apple",
    "spi:description": "Apple",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:langcode": "EN",
    "spi:enterby": "MAXADMIN",
    "spi:settype": "COMPANY"

}
```

### Success Criteria
API executed successfully.
Company Set named Apple created.

### Get Sets Query

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin&oslc.where=setid="APPLE"
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
        "rdf:about": "http://localhost/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin&oslc.where=setid=%22APPLE%22"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_QVBQTEU-"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets"
}
```

### Get Sets
```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets/_QVBQTEU-?_lid=maxadmin&_lpwd=maxadmin
```

Result:
```JSON
{
    "spi:settype_description": "Company Sets",
    "spi:setid": "APPLE",
    "spi:description": "Apple",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:setsid": 9,
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets/_QVBQTEU-",
    "spi:langcode": "EN",
    "spi:enterdate": "2025-09-08T05:27:00+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "1378173",
    "spi:hasld": false,
    "spi:settype": "COMPANY",
    "spi:autoupdate": false
}
```
