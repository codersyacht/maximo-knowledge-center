# Map Manager

### Author Mohamed Jawahar Hussain

## Introduction

Create a Map Manager

## Prerequisite
```mermaid
graph LR
A[Set Content Security Policy] --> B[Grant Object Structure Permission]

## Process Diagram

## Execution Steps

### Set Content Security Policy

- Navigate to System Configuration -> Platform Configuration -> System Properties
- Search for property name **mxe.sec.header.Content_Security_Policy**
- Edit the default value, add *.openstreetmap.org to the img-src parameter.
- Example:
```PROP
img-src 'self' d2qhvajt3imc89.cloudfront.net data: _*.openstreetmap.org_ *.walkme.com *.{{DOMAIN_NAME}} *.trustarc.com *.qualtrics.com
```
- Save

### Object Resouce Permission
