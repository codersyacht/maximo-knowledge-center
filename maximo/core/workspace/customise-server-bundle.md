# Customise Maximo Server Bundle

### Author: Mohamed Jawahar Hussain

## Introduction
Modify Maximo liberty server's server.xml via server bundle changes.

## Prerequisite
Maximo Manage deployed and running successfully.

## Process Diagram

Not applicable

## Execution Steps

Navigate to Suite -> Administration -> Workspace
Select Manage Application
Select Action -> Update Configuration
Click edit icon next to Server bundle.
Disable Server managed option.
Click on view link of the under Additional Properties of the relevant server bundle.
In the Additional server config section place the additional server.xml configuration.

For example to add a new application to the context, place the following content:

```XML
<server>
    <webApplication id="doclinks" contextRoot="/doclinks" location="/tmp/doclinks" name="doclinks" />
</server>
```
Save the changes.
Apply Changes.
The changes will be reconciled and the pods will be restarted.

## Success Metric

The changes take effect upon restart of the pods.

## Next Step

Not applicable.
