# Item Definition

### Author: Mohamed Jawahar Hussain

## Introduction

Define a new item

## Prerequisite

|Action|Reference|
|--|--|
|Define item set|[here](/maximo/docs/administration/sets/01-item-set.md)|

## Process Diagram

```mermaid
graph LR
A[Begin]-->B[Choose Item Set]
B-->C[Create Item]
C-->D{Completed?}
D--> |No| A 
D--> |Yes| E[End]
```

## Execution Steps

### Define Item

[**API**](/maximo/api/inventory/create-item.json)

## Success Metric
