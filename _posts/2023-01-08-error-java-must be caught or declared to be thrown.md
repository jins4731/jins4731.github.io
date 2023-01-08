---
title: java-IOException must be caught or declared to be thrown
author: jins4731
date: 2023-01-08 13:50:00 +0900
categories: [Error, Backend]
tags: [Error]
pin: true
---

# [java] unreported exception IOException; must be caught or declared to be thrown

## 에러 내용

coding test 문제 풀이중 다음과 같은 에러가 났다.

```java
error : unreported exception IOException;
must be caught or declared to be thrown
```

**BufferedReader나 BufferedWriter 와 같은 버퍼를 사용할 때에는 IO 예외처리를 해줘야 한다.**

## 오류 해결

다음과 같이 **메소드에 예외처리**를 해주도록 한다.

```java
public static void main(String[] args) throws IOException {
}
```
