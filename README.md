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