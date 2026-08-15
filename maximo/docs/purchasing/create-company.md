

# Models

### Author: Mohamed Jawahar Hussain

## Introduction



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
D --> E[Add Company Master to Organisation]
E --> F[Select Organisation]
F --> G[Exit]
```

## Execution Steps

### Define Model

- Navigate to Purchasing -> Company Master.
- New Company Master.
- Provide a Company Name and Description.
- Select Currency and Company Set.
- Save
- Click Add Company Master to Organisation in the side navigation.
- Select organisation and click ok.
- Exit.

[API](/maximo/api/purchasing/create-company.json)
  

## Next Step

NA

