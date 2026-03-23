
# GL Account

### Author: Mohamed Jawahar Hussain

## Introduction

## Prerequisite

| Action | Reference |
|----|----|
|Create GL Components|[here](/maximo/finance/chart-of-accounts/01-gl-components.md)|

## Process Diagram

## Process Diagram

```mermaid
graph LR
A[Begin] --> B[Choose Component Cost Center]
B --> C[Choose Component Activity]
C --> D[Choose Resource]
D --> E[Choose Element]
E --> F[Create GL Account]
F --> G[Create GL Account]
```
## Execution Steps

**API**
|Attribute|Value|
|---------|-----|
|URL|/maximo/oslc/os/mxglcomp|
|Method|Post|
|Payload|/maximo/finance/chart-of-accounts/api/create-gl-account.json|

## Next Step

| Action | Reference |
|----|----|
|Create Organization|[here](/maximo/administration/organizations/01-organization-definition.md)|
