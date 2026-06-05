
# Docker Email Server

### Author: Mohamed Jawahar Hussain

## Introduction

Installation of Docker Email server.

## Prerequisite

|Action|Reference|
|--|--|
| Docker Installation |[here](/maximo/docs/administration/sets/01-item-set.md)|

If Docker Email server is already installed, remove the container. 

Replace docker with podman if docker runtime is used.

```CMD
docker rm -f cdy-dms
```
```CMD
docker volume rm dms-data dms-state dms-config
```

## Process Diagram

```mermaid
graph LR

A[Begin] --> B[Configure Domain]
B --> C[Install DMS]
C --> D[Create User Account]
D --> E{Completed?}
E --> |No| D 
E --> |Yes| F[End]
```

## Execution Steps

Edit /etc/hosts file in the system where the docker email server is intended to be installed.
Make the following entry:
```
127.0.0.1       cdy cdy.com
```


**Docker**

```CMD
docker run -d --name cdy-dms -p 3025:25 -p 3143:143 -p 3993:993 --hostname cdy --domainname cdy.com -v dms-config:/tmp/docker-mailserver/ -v dms-data:/var/mail/ -v dms-state:/var/mail-state/ mailserver/docker-mailserver:latest
```

```CMD
docker exec -it cdy-dms setup email add md.jawahar@cdy.com password
```
```CMD
docker exec -it cdy-dms setup email add azmi@cdy.com password
```

**Podman**

```CMD
podman run -d --name cdy-dms -p 3025:25  -p 3143:143 -p 3993:993 -e OVERRIDE_HOSTNAME=cdy -e DOMAINNAME=cdy.com -v dms-config:/tmp/docker-mailserver/ -v dms-data:/var/mail/ -v dms-state:/var/mail-state/ mailserver/docker-mailserver:latest
```
```CMD
podman exec -it cdy-dms setup email add md.jawahar@cdy.com password
```
```CMD
podman exec -it cdy-dms setup email add azmi@cdy.com password
```


## Success Metric

The Docker Email Server container should be up and running.

Replace docker with podman if docker runtime is used.

```CMD
docker ps
```

```
jawahar@MacBookPro codersyacht % docker ps
CONTAINER ID   IMAGE                                 COMMAND                  CREATED             STATUS             PORTS                                                                                                                                       NAMES
df478f467058   mailserver/docker-mailserver:latest   "/usr/bin/dumb-init …"   About an hour ago   Up About an hour   110/tcp, 465/tcp, 587/tcp, 993/tcp, 995/tcp, 4190/tcp, 0.0.0.0:3025->25/tcp, [::]:3025->25/tcp, 0.0.0.0:3143->143/tcp, [::]:3143->143/tcp   maximo-dms
```

Should be able to connect to both SMTP and IMAP port.

```CMD
telnet localhost 3143
```
```CMD
telnet localhost 3025
```

## Next Steps

|Action|Reference|
|--|--|
| Thunderbird Mail Client Installation |[here](/devops/email-server/thunderbird.md)|

