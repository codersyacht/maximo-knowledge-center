
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
wget -O webprofile-8.zip https://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/wasdev/downloads/wlp/24.0.0.11/wlp-webProfile8-24.0.0.11.zip
```
```CMD
unzip webprofile-8.zip
```
```CMD
rm webprofile-8.zip
```

Root directory of Liberty server is /home/admin/apps/wlp.

### Navigate to bin folder and create server

```CMD
cd /home/admin/apps/wlp/bin
```
```CMD
./server create manage
```
