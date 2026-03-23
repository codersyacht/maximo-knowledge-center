# Chart of Accounts

## Introduction

Maximo GL components are segments that structure the General Ledger (GL) account code, allowing for detailed cost tracking and integration with financial systems.

## Prerequisite

No prerequisite required.

## Process Diagram

```mermaid
graph LR
A[Begin] --> B[Create Component Cost Center]
B --> C[Create Componenet Activity]
C --> D[Componenet Resource]
D --> E[Component Element]
E --> F[End]

### Create GL Componenet Cost Center

## Execution Steps

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
