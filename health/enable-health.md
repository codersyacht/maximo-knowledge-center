# Health

### Author: Mohamed Jawahar Hussain

## Introduction

Enabling Health Application

## Prerequisite

Health Application Installed.

## Execution Steps

**Security Group**

- Navigate to Suite -> Access and Usage -> Security Groups
- Search and open Maxadmin group.
- Go to Application.
- Filter _Assets & Locations_.
- Ensure all Permissions are enabled (especially _Accss to Reliability Engineering_). 

**Security Group (Manage)**

- Navigate to Manage -> Security -> Security Group (Manage)
- Search and open Maxadmin group.
- Navigate to Applications.
- Search for _Assets & locations_. Actions -> Grant Listed Applications -> All Above.
- Under Options for Assets & locations, check Grant Access is enabled. Actions -> Manage/Apply Template -> Actions -> Apply Template.

**Access the application**

```
<host:port>/maximo/oslc/graphite/relengineer/index.html#/health
```

