## Staring and Stopping Liberty Server

Setup directory /home/admin/apps (This is subjective to the user and environment).

**Set Java Path**

[Set Java Path](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/java/java-path.md)

**Start**
```CMD
/home/admin/apps/wlp/bin/server start manage
```
Note the server start status in _/home/admin/apps/wlp/usr/servers/maximo/logs/messages.log_

**Stop**
```CMD
/home/admin/apps/wlp/bin/server stop manage
```
