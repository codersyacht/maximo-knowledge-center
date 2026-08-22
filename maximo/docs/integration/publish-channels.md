# Create Publish Channel

### Author: Mohamed Jawahar Hussain

## Introduction

Create a publish channel. The publish channel is a template that defines the object and it's format to be published.

## Prerequisite

Not applicable

## Process Diagram

```mermaid
graph LR
[A]Define Publish Channel --> B[Select Operation]
B --> C[Select Object Structure]
C --> D[Select Adapter]
D --> E[Enable Publish JSON]
E --> F[Save]
F --> G[Enable Message Tracking & Store Message]
G --> Enable Event Listener

