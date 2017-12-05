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


## utfmd4 설정
### 서버 character-set 확인
``` mysql
show variables where variable_name like 'character\_set\_%' or variable_name like 'collection%';
```

### 테이블 변경
``` mysql
ALTER TABLE '테이블명' MODIFY COLUMN '칼럼명' varchar(64) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
alter table '테이블명' default character set = utf8mb4 collate = utf8mb4_unicode_ci;
ALTER DATABASE 'db명' CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci;
```

### 설정파일 추가
my.cnf 
[client]
default-character-set=utf8mb4
[mysqld]
character-set-server = utf8mb4
[mysql]
default-character-set=utf8mb4
