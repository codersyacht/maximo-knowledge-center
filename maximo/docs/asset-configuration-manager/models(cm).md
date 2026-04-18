
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


## Next Step

