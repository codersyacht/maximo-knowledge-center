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

```CMD
cd lang
```
Unzip the required language pack. For example, to install arabic locale, extract MaximoLangPkgXliff_Ar.zip.

```CMD
unzip MaximoLangPkgXliff_Ar.zip
```
There will be two folders namely ar and cs under /home/admin/apps/langpack/lang/tools/maximo.

Copy the ar foldere into 


```CMD
./TDToolkit.sh -addlangar
```
