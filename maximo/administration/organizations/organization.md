## Organizations

### Prerequisite

Maximo installed and manage application accessible. 

### Introduction

n IBM Maximo, an Organization is a foundational data structure that defines how your company—or multiple companies—are represented within the system. It’s not just a label; it’s a container for business rules, financial settings, and operational data.

### Create Organization

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{

    "spi:itemsetid": "Devices",
    "spi:companysetid": "Apple",
    "spi:description": "IBM",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:orgid": "IBM",
    "spi:enterby": "MAXADMIN",
    "spi:category": "STK",
    "spi:active": false,
    "spi:basecurrency1": "USD"
}
```

### Success Criteria
API executed successfully.
Organization IBM created.

### Get Organization 

All Organization:

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization?_lid=maxadmin&_lpwd=maxadmin
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
        "rdf:about": "http://localhost/maximo/oslc/os/mxorganization?_lid=maxadmin&_lpwd=maxadmin"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_RUFHTEVOQQ--"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_RUFHTEVTQQ--"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_RUFHTEVVSw--"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_TEdUOTk5"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_SUJN"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxorganization"
}
```

Specific Organization:

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization?oslc.where=orgid="IBM"&_lid=maxadmin&_lpwd=maxadmin
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
        "rdf:about": "http://localhost/maximo/oslc/os/mxorganization?oslc.where=orgid=%22IBM%22&_lid=maxadmin&_lpwd=maxadmin"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxorganization/_SUJN"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxorganization"
}
```

### Get Organization By Id
```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization/_SUJN?_lid=maxadmin&_lpwd=maxadmin
```

Result:
```JSON
{
    "address_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/address",
    "spi:itemsetid": "DEVICES",
    "site_collectionref": "http://localhost/maximo/oslc/os/mxorganization/_SUJN/site",
    "spi:description": "IBM",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:orgid": "IBM",
    "rdf:about": "http://localhost/maximo/oslc/os/mxorganization/_SUJN",
    "spi:enterdate": "2025-09-08T05:29:39+00:00",
    "spi:enterby": "MAXADMIN",
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "spi": "http://jazz.net/ns/ism/asset/smarter_physical_infrastructure#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "_rowstamp": "1378887",
    "spi:category": "STK",
    "spi:companysetid": "APPLE",
    "spi:active": false,
    "spi:organizationid": 8,
    "spi:basecurrency1": "USD"
}
```
