
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

**Manage Attachment Folders**

Navigate to the relevant application for which attachment and print is required. example: work order tracking.
Navigate to More Actions -> Attachmenet Library/Folders -> Manage Folders.
Replace all DOCLINKS path to /tmp/doclinks. For example, for assist, replace the existing Default File Path to /tmp/doclinks/assist.
Click OK and complete.

## Success Criteria

Create a new transaction. For example, a new workorder.
Under Attachments -> Add New Attachments -> Add New File.
Browse for a small jpg file, attach and click OK.
Click on View attachments and click Document. The document should be downloaded.
The attached file should be present in /tmp/doclinks/images within the pod.
Click _Print With Attachments_ on the top right hand side corner.
A dialog box should appear stating the following:
```
BMXAA5300I - A total of 1 attached document(s) have been found, out of which 1 document(s) are printable. Would you like to print them with this report?
```
Click Yes.
The pdf with image should be available now.

