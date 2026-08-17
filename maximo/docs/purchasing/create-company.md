

# Create Company

### Author: Mohamed Jawahar Hussain

## Introduction

A company is a vendor from whom the prganization purchases items.

## Prerequisite

## Prerequisite

| Action  | Reference |
|--------|-------|
|Create Company Set.|[here](/maximo/docs/administration/sets/02-company-set.md)|


## Process Diagram

```mermaid
graph LR
A[Define Company] --> B[Select Currency]
B --> C[Select Company Set]
C --> D[Save]
D --> E[Exit]
```

## Execution Steps

### Define Model

- Navigate to Purchasing -> Company Master.
- New Company Master.
- Provide a Company Name and Description.
- Select Currency and Company Set.
- Save

[API](/maximo/api/purchasing/create-company.json)
  

## Next Step

NA
| Action  | Reference |
|--------|-------|
|Add Company to Organization|[here](/maximo/docs/purchasing/add-company-to-org.md)|
