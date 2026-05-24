

```CMD
docker run -d --name maximo-dms -p 3025:25 -p 3143:143 --hostname maximo --domainname maximo.com  mailserver/docker-mailserver:latest
```

```CMD
docker exec -it local-dms setup email add md.jawahar@maximo.com pass123
```

```CMD
docker exec -it local-dms setup email add azmi@maximo.com pass123
```
