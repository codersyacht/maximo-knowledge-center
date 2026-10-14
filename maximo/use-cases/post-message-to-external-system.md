# Integration - Post Message to External System

### Author: Mohamed Jawahar Hussain

## Introduction

Post message to an external JMS queue when a work order is created.

## Prerequisite

- JMS Server configured and running.
- Maximo configured to function as JMS client.

## Process Diagram

## Execution Steps

The endpoint is the external system to which message is to be posted.
Complete endpoint definition by following the instruction [here](/maximo/docs/integration/endpoints.md)

Configure the Publish channel that defines which object to publish. Ensure to provide the object structure as **MXWO**. Follow the instructions [here](/maximo/docs/integration/publish-channels.md)

Configure the External System binding the Endpoint and the Publish Channel following the instructions [here](/maximo/docs/integration/external-systems.md)

## Success Criteria

Create a workorder.
The message will be sent to SQOUT queue. 
JMS consumer will pick the message.
The message will be reposted to the external queue.

```JSON
"apptrequired":false,"_translangcode":"EN","historyflag":false,"aos":false,"estservcost":0.0,"pluscismobile":false,"parentchgsstatus":true,"plusatermactioncomp":false,"lms":false,"istask":false,"href":"http:\/\/localhost\/maximo\/oslc\/os\/mxwo\/_QkwvMTAwMw--","estatapprmatcost":0.0,"plusaispminactive":false,"pluscloop":false,"actmatcost":0.0,"actlabhrs":0.0,"nestedjpinprocess":false,"estatapprtoolcost":0.0,"hasfollowupwork":false,"actservcost":0.0,"flowactionassist":false,"ignorediavail":false,"reqasstdwntime":false,"estmatcost":0.0,"pluspporeq":false,"pluspallowquote":false,"status":"WAPPR","plusaisjprev":false,"estlabhrs":0.0,"esttoolcost":0.0,"reportedby":"MAXADMIN","los":false,"estoutlabcost":0.0,"plusadef":false,"plusahasdiscrepancy":false,"disabled":false,"outmatcost":0.0,"estdur":0.0,"plusapmrevisionnum":0,"plusaaddjcinprocess":false,"changeby":"MAXADMIN","plusaispmrev":false,"plusassi":false,"interruptible":false,"estlabcost":0.0,"plusawpresetpmdeadline":true,"estatapprintlabhrs":0.0,"statusdate":"2026-10-14T09:18:54+00:00","wonum":"1003","downtime":false,"workorderid":133430,"_event":true,"plussisgis":false,"acttoolcost":0.0,"actlabcost":0.0,"actoutlabcost":0.0,"estatapprlabhrs":0.0,"estatapprservcost":0.0,"estatapprlabcost":0.0,"lastcopylinkdate":"2026-10-14T09:18:57+00:00","pluspallowquotelabor":false,"ignoresrmavail":true,"plustdriverreq":false,"outtoolcost":0.0,"estatapproutlabhrs":0.0,"estatapprintlabcost":0.0,"siteid":"BL","plustworkassign":false,"totalworkunits":0.0,"suspendflow":false,"status_description":"Waiting on approval","woisswap":false,"actintlabhrs":0.0,"woacceptscharges":true,"plustrepord":false,"plusamsg3":false,"plusawprevisionnum":0,"repairlocflag":false,"changedate":"2026-10-14T09:18:57+00:00","chargestore":false,"woclass_description":"Work Order","outlabcost":0.0,"orgid":"CDY","pluspbillapproved":false,"plustmptype_description":"Motor-pool assignment","woclass":"WORKORDER","actoutlabhrs":0.0,"_id":"BL-1003","plustlock":false,"inctasksinsched":true,"plustfullcoverage":false,"flowcontrolled":false,"ams":false,"reportdate":"2026-10-14T09:18:54+00:00","_action":"Add","plusacpcp":false,"estatapproutlabcost":0.0,"newchildclass":"WORKORDER","plusamsi":false,"djpapplied":"NO","pluspallowquotematerial":false,"estoutlabhrs":0.0,"isquickreported":0,"plustmptype":"MOTORPOOL","actintlabcost":0.0,"ai_usefortraining":false,"pluspallowquoteservice":false,"estintlabhrs":0.0,"plusaaccess":false,"statusiface":false,"milestone":false,"plustactmpprice":0.0,"wogroup":"1003","estintlabcost":0.0,"haschildren":false,"plustmalert":true}
```

