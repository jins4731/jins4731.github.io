---
title: Docker로 tomcat, ubuntu 컨테이너 설치해보기
author: jins4731
date: 2023-01-07 11:20:00 +0900
categories: [개발도구, Docker]
tags: [Docker]
pin: true
---

# Docker 로 tomcat, ubuntu 컨테이너 만들기

## Docker로 Ubuntu 컨테이너 만들기

### curl 설치

```bash
sudo apt update / yum update
sudo apt install curl / yum install curl
```

> sudo: apt: command not found
> -> apt 말고 yum 사용

### 우분투 이미지 가져오기

```bash
docker pull ubuntu:20.04
```

### 우분투 이미지 컨테이너로 생성하기 (run 먼저 안됨)

```bash
docker run -d -it --name ub ubuntu:20.04/bin/bash
docker run --name ub ubuntu:20.04/bin/bash
docker run --name ub docker.io/ubuntu:20.04/bin/bash
```

### 도커 우분투 이미지로 컨테이너 생성 (create 로 먼저 생성)

```bash
docker create --name ub ubuntu
docker create --name ub docker.io/ubuntu
```

### 생성된 컨테이너 조회

```bash
docker ps -a
```

### 생성된 컨테이너 실행 (status: existed 로 실행)

```bash
docker start ub
```

### 컨테이너 삭제

```bash
docker rm ub
```

### 도커 우분투 이미지로 컨테이너 생성

```bash
docker create -it --name ub docker.io/ubuntu
#(-it 옵션 추가 : 컨테이너 실행 후 , status up 상태로)
```

### 우분투 컨테이너 접속

```bash
docker exec -it ub /bin/bash
```

## 자바 설치

### curl 설치

```bash
# curl 설치
apt update
apt install curl
```

### 자바 다운로드

winscp 이용해서 jdk, tomcat 옮기고, cp 명령어 사용하여 컨테이너에 파일 복사 한다.
경로는 우분투 내 /usr/local 안에 넣기

### 컨테이너 파일 복사

```bash
docker cp /root/jdk/jdk1.8.0_341 ub:/usr/local/
#docker cp /home/jdk/jdk1.8.0_341 ub:/usr/local/
#docker cp /home/tomcat9/tomcat-9.0 ub:/usr/local/
#docker cp /home/wise.rnd.ds.1.war ub:/usr/local/
#docker cp /home/editds ub:/usr/local/

#docker cp /home/wise.rnd.ds.1 ub:/root/jeus7
#docker cp /home/editds ub:/root/jeus7
#docker cp /home/editds wiseolap:/root/jeus7
```

### 자바 링크 생성

```bash
ln -s ./jdk1.8.0_341 java
```

### 자바 위치 확인

```bash
whereis java
```

### vi 에디터 설치

```bash
apt install vim
```

> 안될떄,
> apt-get update
> centos 에서
> `# yum install vim-enhanced`

## 톰캣 설치

### Tomcat 설치

```bash
cd ~
curl -OL "http://apache.tt.co.kr/tomcat/tomcat-9/v9.0.38/bin/apache-tomcat-9.0.38.tar.gz"
# 또는
curl -OL "http://mirror.navercorp.com/apache/tomcat/tomcat-9/v9.0.36/bin/apache-tomcat-9.0.36.tar.gz"
```

### 압축 풀기

```bash
tar xvf apache-tomcat-9.0.65.tar.gz
```

### 톰캣 이동

```bash
mv apache-tomcat-9.0.36 /usr/local/
```

### 톰캣 링크 설정

```bash
ln -s ./apache-tomcat-9.0.36 tomcat
```

### tomcat 폴더 이름 변경

```bash
mv apache-tomcat-9.0.65 tomcat-9.0
```

### 톰캣 Ubuntu 컨테이너로 파일 복사

```bash
docker cp /root/tomcat9/tomcat-9.0 ub:/usr/local/
```

### 톰캣 링크 설정

```bash
ln -s ./tomcat-9.0 tomcat
```

### 환경변수 vi 에디터로 편집

```bash
vi /root/.bashrc

export CATALINA_HOME=/usr/local/tomcat
export PATH=$PATH:$CATALINA_HOME/bin
export CALSS_PATH=$CLASS_PATH:$JAVA_HOME/lib/tools.jar:$JAVA_HOME/jre/lib/ext:$CATALINA_HOME/lib/jsp-api.jar:$CATALINA_HOME/lib/servlet-api.jar
export LC_ALL=C.UTF-8

#을 추가한다. PATH랑 CLASS_PATH는 뒤에 : 으로 추가하면 되니까 이렇게 하면 된다.

export JAVA_HOME=/usr/local/java
export CATALINA_HOME=/usr/local/tomcat
export PATH=$PATH:$JAVA_HOME/bin/:$CATALINA_HOME/bin
export CALSS_PATH=$CLASS_PATH:$JAVA_HOME/lib/tools.jar:$JAVA_HOME/jre/lib/ext:$CATALINA_HOME/lib/jsp-api.jar:$CATALINA_HOME/lib/servlet-api.jar
export LC_ALL=C.UTF-8
```

### 설정 적용하기

```bash
source /root/.bashrc
```

### 톰캣 실행 (기본 포트 8080)

```bash
$CATALINA_HOME/bin/startup.sh
```

### 톰캣 정지

```bash
$CATALINA_HOME/bin/shutdown.sh
```

## 컨테이너에 Jeus 설치 하기

### 환경 변수 설정

```bash
vi /root/.bashrc

export JAVA_HOME=/usr/local/jdk1.8.0_341
export PATH=$PATH:$JAVA_HOME/bin/
export CLASS_PATH=$CLASS_PATH:$JAVA_HOME/lib
```

### 설정 적용하기

```bash
source /root/.bashrc

##권한 문제
chmod 700 *.sh
chmod 700 /usr/local/java/bin/java

##JEUS 환경변수
export JAVA_HOME=/usr/local/jdk1.8.0_341
export JEUS_HOME=/root/jeus7
export PATH=$JEUS_HOME/bin:$PATH

##JEUS 실행 / 서버 기동 (DAS 기동)
startDomainAdminServer -u administrator -p administrator
서버 중지 (DAS 전체 중지됨)
./stopServer -domain jeus_domain -server server1 -u administrator -p administrator

##Node 매니저 기동
./startNodeManager
```

### 노드 서버 기동 (MS 기동) 이건 안해도됨

```bash
./startManagedServer -domain jeus_domain -server server1 -u administrator -p administrator
```

### DAS 접속

```bash
jeusadmin -u administrator -p administrator
```

### 서버 시작

```bash
start-server -f server1
```

### 어플리케이션 배포

```bash
deploy -path /root/jeus7/wise.rnd.ds.1 -servers server1 -contextPath /editds
deploy -path /root/jeus7/editds -servers server1 -contextPath /editds
```

### 어플리케이션 배포 삭제

```bash
undeploy wise.rnd.ds.1
```

### 어플리케이션 정보

```bash
application-info
```

### 서버 중지

```bash
stop-server -f server1
```

### unzip 설치

```bash
apt install unzip
```

### docker image 허브에 올리기

```bash
docker image tag wiseolap:1.0.0 syjin/wiseolap:1.0.0
docker push syjin/wiseolap:1.0.0
```

### jeus jvm 설정

```bash
add-jvm-option -server server1 -opt "-Dfile.encoding=utf-8"
```
