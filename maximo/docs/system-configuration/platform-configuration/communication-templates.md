# Communication Template

### Author: Mohamed Jawahar Hussain

## Introduction


## Prerequisite

Edit /etc/hosts file in the system where the docker email server is intended to be installed. Make the following entry:
```
9.60.155.138    codersyacht.com mail.codersyacht.com
```

| Syastem Property | Value |
|------------------|-------|
|mxe.esigresetemailfrom|maxadmin@codersyacht.com|
|mail.smtp.host|mail.codersyacht.com|
|mail.smtp.port|3025|
|mail.smtp.ssl.enable|false|
|mail.smtp.starttls.enable|false|
|mxe.smtp.user|maxadmin@codersyacht.com|
|mxe.adminEmail|maxadmin@codersyacht.com|

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
|Send From| maxadmin@codersyacht.com |
|Subject|Service Request :ticketid|
|Message|New Service Request with ticket id: :ticketid has been created.|

Navigate to Recipient tab. Click + symbol next to _Role(s) for Communication Template NOTIFICATION_ Add the following
Role: maxadmin
Enable: To?

Save and activate.
