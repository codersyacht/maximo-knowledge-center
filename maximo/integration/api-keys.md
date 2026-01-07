# Generate API Key For Rest API Calls

- Navigate to Integration -> API Keys
- Click _Add API Key +_
- Search for user MAXADMIN and select the user MAXADMIN.
- Click Create button. The API Key will be created.
- Click _Copy Key_ to copy the APU key. The key will be like _nph4ucvk7gahpbg93tnq5a7ivm9f85o5uerkdvv6_

## Testing the API Key

API can be accessed via two methods.

**Option 1: Using username and password in the URL string.**

- URL:  _http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?_lid=maxadmin&_lpwd=maxadmin_
- Method: GET

**Option 2: Using API Key**

- URL: http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets
- Method: GET
- Http Header: Key: apikey, Value: nph4ucvk7gahpbg93tnq5a7ivm9f85o5uerkdvv6

## Output

```JSON
{
    "prefixes": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
        "oslc": "http://open-services.net/ns/core#"
    },
    "oslc:responseInfo": {
        "rdf:about": "http://localhost/maximo/oslc/os/mxapisets"
    },
    "rdfs:member": [
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_U0VUMQ--"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_U0VUMg--"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_Q09NUFNFVDE-"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_SVQgSVRFTVM-"
        },
        {
            "rdf:resource": "http://localhost/maximo/oslc/os/mxapisets/_REVWSUNFUw--"
        }
    ],
    "rdf:about": "http://localhost/maximo/oslc/os/mxapisets"
}
```


