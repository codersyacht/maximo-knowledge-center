## Access to MX Objects.

In this example, we will make use of MXORGANIZATION object.

While calling the following API, 

http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization?_lid=maxadmin&_lpwd=maxadmin

the below error is noted.

```JSON
{
    "oslc:Error": {
        "oslc:statusCode": "400",
        "spi:reasonCode": "BMXAA9301E",
        "oslc:message": "BMXAA9301E - The user of the transaction is not authorized for Object Structure MXORGANIZATION.  Configure authorization in the object structure application and grant necessary access to the user.",
        "oslc:extendedError": {
            "oslc:moreInfo": {
                "rdf:resource": "http://localhost/maximo/oslc/error/messages/BMXAA9301E"
            }
        },
        "timestamp": "2025-09-08T05:29:57+00:00"
    }
}
```

Navigte to Integration -> Object Structures. Search for MXORGANIZATION Object Structure, and select the object.

In the left sidebar, select Configure Object Structure Security.

Enable Use _Object Structure for Authorization Name?_

Click OK.

Post which _Add/Modify Signature Options_ will be visible.

Navigate to Security -> Security Groups. Search for the relevant group and select. Here we use _maxadmin_.

Select Object Structure. Search for MXORGANIZATION.

Select the object and grant access for Delete, Insert, Read and Save.

Save the configuration.

Restart the Server.
