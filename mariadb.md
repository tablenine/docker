### 서버실행

```sh
docker run --name some-mariadb -v /my/own/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -p3306:3306 -d mariadb:tag --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```



### 클라이언트 접속

```sh
docker run -it --rm mariadb:tag mysql -h호스트 -u아이디 -p패스워드
```



### 덤프

```
docker exec some-mariadb sh -c 'exec mysqldump --all-databases -uroot -p"$MYSQL_ROOT_PASSWORD"' > /some/path/on/your/host/all-databases.sql

docker exec some-mariadb sh -c 'exec mysqldump -uroot -p"$MYSQL_ROOT_PASSWORD" databases' > /some/path/on/your/host/all-databases.sql
```



### 로그 확인

