## Chart of Accounts

### Create GL Componenet Cost Center

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{
  "spi:active": true,
  "spi:compvalue": "0000",
  "spi:userid": "MAXADMIN",
  "spi:orgid": "IBM",
  "spi:glorder": 0,
  "spi:comptext": "0000"
}
```

### Create GL Componenet Activity

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{
  "spi:active": true,
  "spi:compvalue": "000",
  "spi:userid": "MAXADMIN",
  "spi:orgid": "IBM",
  "spi:glorder": 1,
  "spi:comptext": "000"
}
```
### Create GL Component Resource

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxglcomp?_lid=maxadmin&_lpwd=maxadmin
```

```JSON
{
  "spi:active": true,
  "spi:compvalue": "000",
  "spi:userid": "MAXADMIN",
  "spi:orgid": "IBM",
  "spi:glorder": 2,
  "spi:comptext": "000"
}
```
### Create GL Account

```URL
http://maxserver1.fyre.ibm.com:9080/maximo/oslc/os/mxcoa?_lid=maxadmin&_lpwd=maxadmin
```
```JSON
{
    "spi:accountname": "0000 + 000 + 000",
    "spi:orgid": "IBM",
    "spi:glcomp03": "000",
    "spi:glcomp02": "000",
    "spi:active": true,
    "spi:glcomp01": "0000",
    "spi:glaccount": "00000-000-000"
}
```
