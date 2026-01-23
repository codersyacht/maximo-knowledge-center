# Create Item Set

### Author: Mohamed Jawahar Hussain

### Prerequisite:
Manage application installed and running.

## Steps to Create Item Set

URL: http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets
Method: Post
Body:
```JSON
{
    "spi:settype_description": "Deviced",
    "spi:setid": "Devices",
    "spi:description": "Devices",
    "spi:dfltitemstatus_description": "Active",
    "spi:dfltitemstatus": "ACTIVE",
    "spi:langcode": "EN",
    "spi:enterby": "MAXADMIN",
    "spi:settype": "ITEM"

}
```

### Result
Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for Devices. If the API is successfully executed, the device set will be visible,
