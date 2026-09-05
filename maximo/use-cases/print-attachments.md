
# Print Attachments

### Author: Mohamed Jawahar Hussain

## Introduction

Configure and execute print attachments.

## Prerequisites

|Action|Reference|
|-------|--------|
|||

## Process Diagram


## Execution Steps

**System Properties**

|Property|Value|
|---------|----|
|mxe.doclink.doctypes.defpath|/tmp/doclinks|
|mxe.doclink.doctypes.topLevelPaths|/tmp/doclinks|
|mxe.doclink.path01|/tmp/doclinks=https://max-all.manage.codehub.dev.fyre.ibm.com/doclinks 

**Customise Server Bundle**

```XML
<server>
    <webApplication id="doclinks" contextRoot="/doclinks" location="/tmp/doclinks" name="doclinks" />
</server>
```


