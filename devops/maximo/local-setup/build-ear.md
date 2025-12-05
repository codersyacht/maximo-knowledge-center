## Building Maximo EAR

**Setting up environment for development mode**

Navigate to the following location.

```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all/maximouiweb/webmodule/WEB-INF_
```
rename web.xml to web-original.xml

rename web-dev.xml to web.xml.

```CMD
mv web.xml web-original.xml
```
```CMD
mv web-dev.xml web.xml
```

Perform the same action under the following directories as well. 

```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all/maxrestweb/webmodule/WEB-INF
```
```CMD
mv web.xml web-original.xml
```
```CMD
mv web-dev.xml web.xml
```
```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all/mboweb/webmodule/WEB-INF
```
```CMD
mv web.xml web-original.xml
```
```CMD
mv web-dev.xml web.xml
```
```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all/meaweb/webmodule/WEB-INF
```
```CMD
mv web.xml web-original.xml
```
```CMD
mv web-dev.xml web.xml
```
**EAR Build**

Navigate to the following directory.

```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/
```

Execute the folllowing command.

```CMD
./maximo-all.sh
```

The above command will generate maximo-all.ear in the following directory:
```CMD
/home/admin/apps/SMP/maximo/deployment/was-liberty-default/deployment/maximo-all/maximo-all-server/apps
```
