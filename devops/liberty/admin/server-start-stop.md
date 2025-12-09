## Staring and Stopping Liberty Server

Setup directory /home/admin/apps (This is subjective to the user and environment).

**Set Java Path**

[Set Java Path](https://github.ibm.com/maximo-application-suite/knowledge-center/blob/main/devops/system/04-Java-Path.md)

**Start**
```CMD
/home/admin/apps/wlp/bin/server start manage
```
Note the server start status in _/home/admin/apps/wlp/usr/servers/maximo/logs/messages.log_

**Stop**
```CMD
/home/admin/apps/wlp/bin/server stop manage
```
