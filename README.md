# MeshCentral2

```
docker run --name meshcentral \
-p 25:25/tcp -p 80:80/tcp -p 443:443/tcp -p 4443:4443/tcp -p 27017-27018/tcp \
-v meshcentral-data:/home/meshserver/meshcentral-data \
-e PORT=443 -e REDIRPORT=80 -e MPSPORT=4443 -e EMAIL=mail@ -e HOST=host.ltd -e SMTP=smtp.host.ltd \
-e USER=smtp@user \
-e PASS=smtppass! \
-e DB=netdb -e MONGODB="mongodb://127.0.0.1:27017/meshcentral" -e MONGODBCOL="meshcentral" \
--restart=always --hostname=mesh.host.name -d technoexpress/meshcentral2
```

Additionally passing the following environment options at run time controls operations:
```
`–e PORT=443 `
`–e REDIRPORT=80`
`–e MPSPORT=4443`
`–e EMAIL=mail@`
`–e HOST=host.ltd`
`–e SMTP=smtp.host.ltd`
`–e USER=smtp@user`
`–e PASS=smtppass!`
`–e DB=netdb`
`–e MONGODB="mongodb://127.0.0.1:27017/meshcentral"`
`–e MONGODBCOL="meshcentral"`
```

If nothing is passed i,n the above are defaults, and USER, HOST, and EMAIL change to support@ detected docker HOSTNAME, and no password.


## This build also assume reverse proxy is setup. This build setup uses https://github.com/adi90x/rancher-active-proxy

```
-v /nginx/rancher-active-proxy/letsencrypt/archive/mesh.host.name:/etc/letsencrypt/archive/mesh.host.name \
-l rap.host=mesh.host.name \
-l rap.le_host=mesh.host.name \
-l rap.https_method=noredirect \
```

# Docker Hub

https://hub.docker.com/r/technoexpress/meshcentral2/builds/ automatically builds the latest changes into images which can easily be pulled and ran with a simple docker run command. 