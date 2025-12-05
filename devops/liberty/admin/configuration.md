# Configure Liberty Server For Maximo

### Author: Jawahar

## Prerequisite
[Liberty Setup](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/admin/install.md)

**JVM Properties**

Navigate to the following directory.

```CMD
cd /home/admin/apps/wlp/usr/servers/manage
```

Create a file named jvm.options with the following content.

[jvm.options](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/maximo/local-setup/artifact/jvm.options)

**Server Properties**

Navigate to the following directory

```CMD
cd /home/admin/apps/wlp/usr/servers/manage
```

Update the server.xml with the following content.

[server.xml](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/maximo/local-setup/artifact/server.xml)
