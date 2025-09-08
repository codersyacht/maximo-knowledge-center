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
