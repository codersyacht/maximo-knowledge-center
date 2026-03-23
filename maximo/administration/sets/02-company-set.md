# Company Sets

### Author: Mohamed Jawahar Hussain

## Prerequisite
No prerequisite required.

## Introduction

A Company Set is a collection of company records that can be accessed by multiple organizations. This allows centralized control over vendor and business partner information, improving consistency and reducing duplication.

## Process Diagram

```mermaid
graph LR
A[Begin] -->B[ Choose Set Type as Company]
B --> C[Create Company Set]
C --> E[End]
```

## Execution Steps

### Create Company Set

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets|
| Method | POST  |
| Payload | [here](/maximo/administration/sets/api/create-company-payload.json) |


## Success Metric

- API executed successfully.
- Company Set named Apple created.

  Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for Apple set. If the API is successfully executed, the Apple set will be visible.

## Get Sets Query

```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets?oslc.where=setid="CDYCSET"
```

Result:
```JSON

```

## Get Set
```URL
http://codehub1.fyre.ibm.com:9080/maximo/oslc/os/mxapisets/_Q0RZQ1NFVA--
```

Result:
```JSON

```
