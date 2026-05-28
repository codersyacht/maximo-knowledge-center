# Communication Template

### Author: Mohamed Jawahar Hussain

## Introduction


## Prerequisite


| Syastem Property | Value |
|------------------|-------|
| |Attributes|Value| md.jawahar@maximo.com|
|mxe.esigresetemailfrom|md.jawahar@maximo.com|
|mail.smtp.host|maximo.com|
|mail.smtp.port|3025|
|mail.smtp.ssl.enable|false|
|mail.smtp.starttls.enable|false|
|mxe.smtp.user|md.jawahar@maximo.com|
|mxe.adminEmail|md.jawahar@maximo.com|

## Process Diagram


## Execution Steps

- Navigate to System Configuration -> Platform Configuration -> Communication Templates -> New Communication Template.
- Create a new Communication Template with the following configuration.

|Attributes|Value|
|-----------|----|
|Template|NOTIFICATION|
|Description|NOTIFICATION|
|Applies To| SR|
|Accessible From| ALL |
|Send From| md.jawahar@maximo.com |
|Subject|WorkOrder Notification|
|Message|Work Order Notification|

Navigate to Recipient tab. Click + symbol next to _Role(s) for Communication Template NOTIFICATION_ Add the following
Role: maxadmin
Enable: To?

Save and activate.
