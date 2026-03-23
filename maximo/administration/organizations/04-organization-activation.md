

```mermaid
gragh LR
A[Begin] --> B[Choose Organization]
B --> C{Clearing Account Selected?}
C --> |Yes|D[Activate Organization]
C--> |No| E[Exit]
D --> E
```

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxorganization/_Q0RZ
```

```JSON
{
    "spi:active": true
}
```
