# Company Sets

### Author: Mohamed Jawahar Hussain

### Prerequisite

Manage application installed and running.

## Introduction

A Company Set is a collection of company records that can be accessed by multiple organizations. This allows centralized control over vendor and business partner information, improving consistency and reducing duplication.

## Create Company Set

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{
    "spi:settype_description": "IBMComp",
    "spi:setid": "IBMComp",
    "spi:description": "IBMComp",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:langcode": "EN",
    "spi:enterby": "MAXADMIN",
    "spi:settype": "COMPANY"

}
```

## Success Criteria

- API executed successfully.
- Company Set named Apple created.

  Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for IBMComp set. If the API is successfully executed, the IBMComp set will be visible.

## Get Sets Query

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?oslc.where=setid="IBMComp"
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
        "rdf:about": "http://localhost/maximo/oslc/os/mxapisets?oslc.where=setid=%22IBMComp%22"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_SUJNQ09NUA--"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets"
}
```

## Get Set
```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets/_SUJNQ09NUA--
```

Result:
```JSON
{
    "spi:settype_description": "Company Sets",
    "spi:setid": "IBMCOMP",
    "spi:description": "IBMComp",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:setsid": 10,
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets/_SUJNQ09NUA--",
    "spi:langcode": "EN",
    "spi:enterdate": "2026-02-21T13:43:11+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "5515324",
    "spi:hasld": false,
    "spi:settype": "COMPANY",
    "spi:autoupdate": false
}
```
