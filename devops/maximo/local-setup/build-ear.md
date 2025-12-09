# Building Maximo EAR

### Author: Jawahar

### Outline:

There are 5 webmodules located in the directory _/home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all_.

Modules:
- maximouiweb
- maxrestweb
- mboejb
- mboweb
- meaweb

The maximouiweb, maxrestweb, mboweb, meaweb are web modules. The mboejb is an ejb module. The 4 web modules have files web-dev.xml and web.xml. The web.xml has to be replaced with web-dev.xml in each of these modules to deploy maximo in development mode.

### Setting up environment for development mode

**maximouiweb**

```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all/maximouiweb/webmodule/WEB-INF
```

```CMD
mv web.xml web-original.xml
```
```CMD
mv web-dev.xml web.xml
```

**maxrestweb**

```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all/maxrestweb/webmodule/WEB-INF
```
```CMD
mv web.xml web-original.xml
```
```CMD
mv web-dev.xml web.xml
```

**mboweb**

```CMD
cd /home/admin/apps/SMP/maximo/deployment/was-liberty-default/config-deployment-descriptors/maximo-all/mboweb/webmodule/WEB-INF
```
```CMD
mv web.xml web-original.xml
```
```CMD
mv web-dev.xml web.xml
```

**meaweb**

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
