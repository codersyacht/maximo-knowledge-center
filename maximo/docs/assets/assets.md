# Create Assets

### Author: Mohamed Jawahar Hussain

## Introduction

Create a standalone asset.

## Prerequisite

|Action | Reference|
|-------|----------|
|Define Item|[here](/maximo/docs/inventory/item-definition.md)|
|Organization Site Activation|[here](/maximo/docs/administration/organization/05-organization-site-activation.md)|

## Process Diagram

A[Define Asset] --> B{Is Rotating?}
B --> |No| C[Save Asset]
B --> |Yes| D[select Rotating Item]
D --> C

