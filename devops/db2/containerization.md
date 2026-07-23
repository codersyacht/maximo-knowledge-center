
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

'''

In this setup the version used is DB2_Svr_11.5_Linux_x86-64.tar.gz
Download location:
DB2 Download
part number: CC1U0ML

Copy the DB2_Svr_11.5_Linux_x86-64.tar.gz file into /home/admin/apps/db2.

Copy the db2server.rsp file into /home/admin/apps/db2. The file is available [here](/devops/db2/artifacts/db2server.rsp).

From within /home/admin/apps/db2 execute the following command:
```CMD
docker build -t DB2 .
```
```CMD
docker run -idt --privileged --name DB2  -v db2data:/database -p 50000:50000 DB2
```
```CMD
docker exec -it DB2 bash
```

Create database using the instructions [here](/devops/db2/create-db.md)
Configure the database using the instruction [here](devops/db2/configuration.md)

enter exit, to exit from the container.

Save the container.
```CMD
docker commit DB2 codersyacht/maximo-db2-linux:base
```
```CMD
docker push codersyacht/maximo-db2-linux:base
```
To pull the container:
```CMD
docker pull codersyacht/maximo-db2-linux:base
```
Run the container.
```CMD
docker run -idt --privileged --name db2server -v db2data:/database -p 50000:50000  codersyacht/maximo-db2-linux:base
```
Go into the container
```CMD
docker exec -it db2server bash
```
Execute the following:
```CMD
su db2inst1
```
```
db2start
```
Enter exit to exit from the container.


