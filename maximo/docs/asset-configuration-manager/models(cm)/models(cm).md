
# Models

### Author: Mohamed Jawahar Hussain

## Introduction



## Prerequisite



## Process Diagram

```mermaid
graph LR
A[Define Model] --> B[Create Build Item]
B --> C[Select CM Item]
C --> D{Crete Build Item}
D -->|Yes|B
D -->|No| E[Configuration]
E --> F[Build Hierarchy]
F --> G[Save]
G --> H[Exit]
```

## Execution Steps

### Create Model

- Navigate to Asset Configuration Manager (CM) -> Models (CM)
- New Model
- Provide a Model name.
- Save

[API](/maximo/api/asset-configuration-manager/models(cm)%20/create-model.json)
  

## Next Step

