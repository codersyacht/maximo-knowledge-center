# Site

### Author: Mohamed Jawahar Hussain

### Prerequisite

Organization defined.

```mermaid
graph LR
A[Begin] --> B[Choose organization]
B --> C[Create site]
C --> D{Is Org Active?}
D --> |Yes| E[Activate Site]
D --> |No| F{Continue?}
E --> F
F --> |Yes|C
F --> |No| G[End]
```

## Introduction

A site is a division within an organization that maintains certain data independently from other sites.”

## Create Site

[**API**](/maximo/api/administration/organization/create-site.json)

## Success Criteria
API executed successfully.
Site BL created.

### Find Site

[**API**](/maximo/api/administration/organization/find-site.json)

### Get Site:

[**API**](/maximo/api/administration/organization/get-site.json)

## Next Step

|Action|Reference|
|------|---------|
|Activate Site| /maximo/docs/administration/organization/05-organization-site-activation.md |
