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
```

## Execution Steps

### Create GL Components

| Action    | Reference  |
|----------|------------|
| Create GL Component Cost Center | [here](/maximo/finance/chart-of-accounts/api/create-gl-component-cost-center.json) |
| Create GL Component Activity | [here](/maximo/finance/chart-of-accounts/api/create-gl-component-activity.json) |
| Create GL Component Resource | [here](/maximo/finance/chart-of-accounts/api/create-gl-component-resource.json) |
| Create GL Component Element | [here](/maximo/finance/chart-of-accounts/api/create-gl-component-element.json) |

## Success Metric


## Next Step

| Action | Reference |
|----|----|
|Create GL Account|[here](/maximo/finance/chart-of-accounts/02-gl-account.md)|
