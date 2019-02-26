## docker sonarqube 

##### 실행
        docker run --name sonarqube -p 9000:9000 -p 9092:9092 -e SONARQUBE_JDBC_USERNAME=root -e SONARQUBE_JDBC_PASSWORD='패스워드' -e SONARQUBE_JDBC_URL=jdbc:mysql://localhost/sonar?useUnicode=true"&"characterEncoding=utf8"&"rewriteBatchedStatements=true"&"useConfigs=maxPerformance -d sonarqube:lts-alpine

###### 로그확인
	docker exec -it sonarqube tail -f /opt/sonarqube/logs/sonar.log 
	docker exec -it sonarqube /bin/sh 
	docker cp sonarqube:/opt/sonarqube/logs/sonar.log ./
