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
  "spi:comptext": "000"
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
  "spi:comptext": "000"
}
```
### Create GL Account

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp
```
```JSON
{
    "spi:accountname": "1000 + 100 + 000",
    "spi:orgid": "IBM",
    "spi:glcomp03": "100",
    "spi:glcomp02": "100",
    "spi:active": true,
    "spi:glcomp01": "1000",
    "spi:glaccount": "1000-100-100"
}
```
