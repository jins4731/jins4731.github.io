---
title: [Postgres] The authentication type 10 issue
author: jins4731
date: 2023-01-06 00:58:00 +0900
categories: [Error, Backend]
tags: [Error]
pin: true
---

# [Postgres] 스프링 연동 시 The authentication type 10 오류

## 에러 내용

org.postgresql.util.PSQLException: The authentication type 10 is not supported. Check that you have configured the pg_hba.conf file to include the client's IP address or subnet, and that it is using an authentication scheme supported by the driver.

위와 같은 오류가 나서, Mart Data 연동이 안되었다.

## 오류 해결

해당 오류는 Postgres 버전과 자바 버전이 맞지 않아서 나는 오류
Postgres JDBC 버전을 다시 다운로드 하여 해결하였다.
[Postgres JDBC 다운로드](https://jdbc.postgresql.org/download/)
