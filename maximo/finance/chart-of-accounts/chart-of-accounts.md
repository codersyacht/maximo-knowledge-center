## Chart of Accounts

### Create GL Componenet Cost Center

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp
```

```JSON
{
  "spi:active": true,
  "spi:compvalue": "1000",
  "spi:userid": "MAXADMIN",
  "spi:orgid": "CDY",
  "spi:glorder": 0,
  "spi:comptext": "1000"
}
```

### Create GL Componenet Activity

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp
```

```JSON
{
  "spi:active": true,
  "spi:compvalue": "100",
  "spi:userid": "MAXADMIN",
  "spi:orgid": "CDY",
  "spi:glorder": 1,
  "spi:comptext": "100"
}
```
### Create GL Component Resource

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp
```

```JSON
{
  "spi:active": true,
  "spi:compvalue": "100",
  "spi:userid": "MAXADMIN",
  "spi:orgid": "CDY",
  "spi:glorder": 2,
  "spi:comptext": "100"
}
```

### Create GL Component Element

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp
```

```JSON
{
  "spi:active": true,
  "spi:compvalue": "100",
  "spi:userid": "MAXADMIN",
  "spi:orgid": "CDY",
  "spi:glorder": 3,
  "spi:comptext": "100"
}
```

### Create GL Account

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp
```
```JSON
{
    "spi:accountname": "1000 + 100 + 100 + 100",
    "spi:orgid": "CDY",
    "spi:glcomp01": "1000",
    "spi:glcomp02": "100",
    "spi:glcomp03": "100",
    "spi:glcomp04": "100",
    "spi:active": true,
    "spi:glaccount": "1000-100-100-100"
}
```
