# Installing a new Locale

### Author: Jawahar

## Introduction

Installing locale on Maximo.

## Prerequisite

lang.zip should be downloaded and be made available for installation in the following directory /home/admin/apps/langpack.

## Process Diagram

## Execution Steps

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

There will be two folders namely ar and cs under /home/admin/apps/langpack/lang/tools/maximo.

Copy the ar foldere into 


```CMD
./TDToolkit.sh -addlangar
```
