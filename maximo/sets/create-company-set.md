# Create Company Set

### Author: Mohamed Jawahar Hussain

### Prerequisite:
Manage application installed and running.

## Steps to Create Item Set

URL: http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets
Method: Post
Body:
```JSON
{
    "spi:settype_description": "Apples",
    "spi:setid": "Apple",
    "spi:description": "Apple",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:langcode": "EN",
    "spi:enterby": "MAXADMIN",
    "spi:settype": "COMPANY"

}
```

### Result
Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for IBM. If the API is successfully executed, the IBM set will be visible,
