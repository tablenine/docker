### Smex docker

```sh
docker run -i -d --name smexTest -p3925:25 -v D:\www\smex_v1.0:/www/smex smextest:1.0
docker exec -it smexTest /bin/bash
docker exec -it smexTest sh /www/smex/smex_start.sh
docker exec -it smexTest sh /www/smex/smex_stop.sh
docker exec -it smexTest tail -f /data/log/smex.log
docker rm smexTest
```

### WebFm docker

```sh
docker run -i -d --name webfmTest -p39443:443 -v C:\www\webFM_v1.0:/www/webFM webfmtest:1.0
docker exec -it webfmTest /bin/bash
docker exec -it webfmTest . /etc/ssbr.profile
docker exec -it webfmTest sh /www/webFM/webFM_start.sh
docker exec -it webfmTest sh /www/webFM/webFM_stop.sh
docker exec -it webfmTest tail -f  /opt/ssbr/3rdparty/webFM_Int/logs/catalina.out
docker commit  webfmTest webfmtest:1.0
docker rm webfmTest
```

### commit test

```sh
docker run -i -d --name commitss centos:6.9
docker exec -i -t commitss /bin/bash
docker commit  commitss centosjava:1.0
docker stop commitss
docker rm commitss
```

### mysql

```sh
docker run --name mysqltest -p 3306:3306 -v D:\mysql:/var/lib/mysql -v D:\myconfig:/etc/mysql/conf.d  -e MYSQL_ROOT_PASSWORD='password' -d mysql:5.6.37

docker exec -it mysqltest bash
```
