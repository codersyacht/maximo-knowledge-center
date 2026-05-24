

```CMD
mkdir -p /Users/jawahar/codersyacht/docker-mailserver
```

```CMD
chmod -R 777 /Users/jawahar/codersyacht/docker-mailserver
```

```CMD
cd /Users/jawahar/codersyacht/docker-mailserver
```

```CMD
docker run -d --name maximo-dms -p 3025:25 -p 3143:143 --hostname maximo --domainname maximo.com -v "$(pwd)/dms/config/:/tmp/docker-mailserver/"  mailserver/docker-mailserver:latest
```

```CMD
docker exec -it local-dms setup email add md.jawahar@maximo.com password
```

```CMD
docker exec -it local-dms setup email add azmi@maximo.com password
```
