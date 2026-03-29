# Company Sets

### Author: Mohamed Jawahar Hussain

## Introduction

A Company Set is a collection of company records that can be accessed by multiple organizations. This allows centralized control over vendor and business partner information, improving consistency and reducing duplication.

## Prerequisite
No prerequisite required.

## Process Diagram

```mermaid
graph LR
A[Begin] -->B[ Choose Set Type as Company]
B --> C[Create Company Set]
C --> E[End]
```

## Execution Steps

### Create Company Set

[**API**](/maximo/api/administration/sets/create-company.json) |


## Success Metric

- API executed successfully.
- Company Set named Apple created.

  Navigate to the following location in the manage application: Administration -> Sets. In the Sets search for Apple set. If the API is successfully executed, the Apple set will be visible.

 ### Get Sets

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets?oslc.where=setid="CDYCSET" |
| Method | GET  |
| Response | [here](/maximo/administration/sets/api/get-company-set-response.json) |

### Get Specific Set

| Field  | Value |
|--------|-------|
| URL    | /maximo/oslc/os/mxapisets/_Q0RZQ1NFVA-- |
| Method | GET  |
| Response | [here](/maximo/administration/sets/api/get-specific-company-set-response.json) | 

## Next Steps

|Requirement| Refecence |
|------------|-----------|
|Configure Organization|[here](/maximo/administration/organizations/01-organization-definition.md)|

