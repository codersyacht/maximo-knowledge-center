# E-mail Listeners

### Author: Mohamed Jawahar Hussain

## Introduction



## Prerequisite



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

### Configuring E-mail Listener

|Attribute|Value|
|--|--|
|E-mail Address|md.jawahar@maximo.com|
|Description|md.jawahar@maximo.com|
|E-mail password|password|
|Mail Server|maximo.com|
|E-mail Folder|Inbox|
|Administrator E-mail|md.jawahar@maximo.com|
|Preprocessor|psdi.common.emailstner.Preprocessor|
|Object Key Delimiter|##|
|Workflow Process|LSNRBP|
|Schedule|30s|
|Cron Task Name|LSNRCRON|
|Cron Task Instance|LSNR9|
|Protocol|imap|
|Protocol|3143|
|Enable STARTTLS?|Yes|

### E-mail Format

```

#MAXIMO_EMAIL_BEGIN
LSNRACTION=CHANGESTATUS
;
LSNRAPPLIESTO=SR
;
CLASS=SR
;
TICKETID=SRNUM
;
STATUS=INPROG
;
SITEID=BEDFORD
;
LOCATION=CONF100
;
ASSET=DISPL1
;
#MAXIMO_EMAIL_END
```

## Next Steps

Not Applicable
