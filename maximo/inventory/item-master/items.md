## Create Item


```mermaid
graph TB
A[Begin]-->B[Choose Item Set]
B-->C[Create Item]
C-->D{Completed?}
D--> |Yes| E[End]
D--> |No| A 
```

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxitem?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{
    "spi:status": "ACTIVE",
    "spi:itemsetid": "DEVICES",
    "spi:itemnum": "IPhone15",
    "spi:rotating": "Y"
}
```
