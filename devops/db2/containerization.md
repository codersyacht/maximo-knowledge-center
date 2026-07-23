
# DB2 Containerization

### Author: Mohamed Jawahar Hussain

## Introduction

Create a containerized DB2 instance for Maximo.

## Prerequicite.

Docker installation.

###

Create the following directory:

```CMD
mkdir /home/admin/apps/db2
```

Create a file **Dockerfile** with the following content:

```Dockerfile
FROM registry.access.redhat.com/ubi9/ubi:latest

RUN dnf install -y \
    glibc.i686 \
    pam.i686 \
    libstdc++.i686 \
    libaio \
    numactl \
    libxcrypt-compat \
    && dnf clean all

RUN mkdir -p /root/installables/db2

COPY DB2_Svr_11.5_Linux_x86-64.tar.gz /root/installables/db2/

RUN tar -xvf /root/installables/db2/DB2_Svr_11.5_Linux_x86-64.tar.gz -C /root/installables/db2/

COPY db2server.rsp /root/installables/db2/server_dec/

WORKDIR /root/installables/db2/server_dec

RUN ./db2setup -r /root/installables/db2/server_dec/db2server.rsp -f sysreq
```



