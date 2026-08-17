
# Liberty Installation

### Author: Jawahar

### Prerequisite:

[Java Setup](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/java/java-install.md)

[Java Path](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/java/java-path.md)

## Download WebSphere Liberty

Setup directory _/home/admin/apps_ (This is subjective to the user and environment).

Download Liberty Server.

For Maximo use Liberty Server Web Profile 8.

```CMD
wget -O webprofile-8.zip https://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/wasdev/downloads/wlp/26.0.0.5/wlp-webProfile8-26.0.0.5.zip
```
```CMD
unzip webprofile-8.zip
```
```CMD
rm webprofile-8.zip
```

Root directory of Liberty server is /home/admin/apps/wlp.

### Create Server

```CMD
cd /home/admin/apps/wlp/bin
```
```CMD
./server create manage
```
``
cd ../usr/servers/manage/
``
```
mkdir lib
```
```
cd lib
```
curl -L -o wmq.jmsra.rar https://repo1.maven.org/maven2/com/ibm/mq/wmq.jmsra/9.3.2.0/wmq.jmsra-9.3.2.0.rar
```
```
cd ..
```
