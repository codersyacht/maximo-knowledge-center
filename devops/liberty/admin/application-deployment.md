## Application Deployment

## Prerequisite

If maximo application is already deployed, stop the server and remove them.

```CMD
cd /home/admin/apps/webprofile-8/bin
```
```
./server stop manage
```
```CMD
cd /home/admin/apps/webprofile-8/usr/servers/manage/dropins
```
```CMD
rm  -rf maximo-all.ear
```
```CMD
cd /home/admin/apps/webprofile-8/usr/servers/manage/apps/expanded
```
```CMD
rm -rf maximo-all.ear
```

## Maximo Deployment

```CMD
/home/admin/apps/webprofile-8/usr/servers/manage/dropins
```
```CMD
mv /home/admin/apps/SMP/maximo/deployment/was-liberty-default/deployment/maximo-all/maximo-all-server/apps/maximo-all.ear /home/admin/apps/webprofile-8/usr/servers/manage/dropins/maximo-all.ear
```
**Start the Server**

[Start Server](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/admin/server-start-stop.md)
