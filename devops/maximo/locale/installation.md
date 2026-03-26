# Installing a new Locale

### Author: Jawahar

## Introduction

Installing locale on Maximo.

## Prerequisite

lang.zip should be downloaded and be made available for installation in the following directory /home/admin/apps/langpack.

## Process Diagram

```mermaid
graph LR
A[Get Language pack zip] --> B[Extract the pack]
B --> C[Copy the required language to maximo directory]
C --> D[Install]
```

## Execution Steps

### Preparing for the Installation

```CMD
cd /home/admin/apps/langpack
```

```CMD
unzip lang.zip
```

```CMD
cd lang
```

Copy the required language pack to the maximo lang directory and to the maximo directory. For example, for arabic locale, MaximoLangPkgXliff_Ar.zip.

```CMD
cp MaximoLangPkgXliff_Ar.zip /home/admin/apps/SMP/maximo/lang
```
```CMD
cp MaximoLangPkgXliff_Ar.zip /home/admin/apps/SMP/maximo
```

Navigate to cp  /home/admin/apps/SMP/maximo, and unpack the file.

```CMD
cd /home/admin/apps/SMP/maximo
```
```CMD
unzip  MaximoLangPkgXliff_Ar.zip
```

This will create configuration files under /home/admin/apps/SMP/maximo/tools/maximo/ar

### Language Pack Installation

Before executing the languange pack installation, note that L_MAXMENU table has no arabic language populated.

```CMD
cd /home/admin/apps/SMP/maximo/tools/maximo
```

```CMD
./TDToolkit.sh -addlangar
```

### Enabling Language

**Prerequisite**

- Complete the actions in the **Next Step** below before proceeding.
- Login to manage application. Launch Default Information in the top right side corner.
- Change the Locale and Language to ar.


## Next Step

|Action       | Reference   |
|-------------|-------------|
| Rebuild ear | [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/maximo/local-setup/build-ear.md)
| Deploy ear |[here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/liberty/admin/application-deployment.md)|


