---
title: Docker 명령어 정리
author: jins4731
date: 2023-01-07 11:19:00 +0900
categories: [개발도구, Docker]
tags: [Docker]
pin: true
---

# Docker 용어 및 명령어 정리

## Docker 용어

### Docker Image

컨테이너 생성(실행)에 필요한 모든 파일과 설정값을 지닌 것

### Docker Container

이미지(Image)를 실행한 상태

---

## Docker 명령어 정리

```bash
# yum 패키지 업데이트 및 업그레이드
sudo yum -y update
sudo yum -y upgrade

# Docker 설치
sudo yum -y install docker docker-registry

# Yum-utils 업데이트
yum install -y yum-utils

# Dockerce 레포 추가
yum-config-manager --add-repo

# Docker tomcat 설치
docker run tomcat:9.0

# Docker 모든 컨테이너 조회
docker ps -a

# Docker tomcat 실행
docker run --name tomcat -p 8080:8080 tomcat:9.0

# Docker tomcat 컨테이너 삭제
docker rm tomcat

# Docker 컨테이너 접속
docker exec -it tomcat /bin/bash

# 컨테이너에 파일 복사
# Docker cp [로컬 파일위치] [컨테이너명:컨테이너내부주소]
docker cp /root/wise.rnd.ds.1.war tomcat:/usr/local/tomcat/webapps
docker cp /root/editds.war mywebserver:/usr/local/tomcat/webapps

# Docker vi 편집기
apt-get update
apt install vim

# Docker tomcat 재시작
docker restart tomcat

# Docker image 조회
docker images

# Docker 실행중인 컨테이너 접속
# docker attach [옵션] <컨테이너명>

# Docker 컨테이너를 이미지로 만들기
docker commit ub myubuntu:1.0.0
docker commit wiseolap wiseolap:6.4.0

# Docker 이미지를 가지고 새로운 컨테이너 생성(포트 포워드 적용)
# myubuntu 라는 이미지를 가지고 mywebserver 라는 새로운 컨테이너 생성
docker run -it --name mywebserver -p 8080:8080 myubuntu:1.0.0
```

> [Dockerce 레포 추가](https://download.docker.com/linux/centos/docker-ce.repo)
