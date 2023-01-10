---
title: Nodejs-npm 으로 express 설치하기
author: jins4731
date: 2023-01-10 23:49:00 +0900
categories: [Backend, Nodejs]
tags: [Nodejs]
pin: true
---

# nodes js express

## npm 으로 express 설치하기

### npm 이란?

Node Package Manager의 약자로 nodejs의 모듈 관리를 하기 위해 사용

> npm은 nodejs 설치 시 자동으로 설치되어 따로 설치할 필요는 없다.

### npm init

package.json 을 생성하여 node js 관리 프로젝트로 전환, node js 에서 사용하는 모듈들을 패키지로 만들어 관리하고 배포

```bash
#
npm init
# 패키지 이름 지정 (default) enter
# 프로젝트 버전 지정 (default) enter
# descript 설정 (descript 설명란으로 프로젝트의 설명을 기입하면된다) enter
# entry point (default: app.js) enter
# test command (default) enter
# git repository (default) enter
# keywords (default tag 입력가능) enter
# author (본인이름입력) enter 입력
# license 배포할계획이 있을때 사용 (MIT) enter
# 모든 내용확인하고 enter
```

> npm inti을 하고 나면 packge.json 파일이 생성된다.
> npm install 에 필요한 파일이다.

### npm install

패키지를 설치하는 명령어

> [npm 사이트](https://www.npmjs.com/)

```bash
npm install express
```

> npm install 을 하고 나면 설치한 패키지들은 node_modules에 저장된다.
> 또한, packge-lock.js 파일이 추가되고, package.json 파일에 dependecies 속성이 추가된다.

## node js 코드를 express code로 바꿔보자

### nodejs

```javascript
const http = require("http");

function handleRequest(request, response) {
  if (request.url === "/currenttime") {
    response.statusCode = 200;
    response.end("<h1>" + new Date().toISOString() + "</h1>");
  } else if (request.url === "/") {
    response.statusCode = 200;
    response.end("<h1>Hello World!</h1>");
  }
}
const server = http.createServer(handleRequest);

server.listen(3000);
```

### express

```javascript
const express = require("express");
const app = express();

app.get("/currenttime", function (req, res) {
  res.send("<h1>" + new Date().toISOString() + "</h1>");
}); //localhost:3000/currenttime
app.get("/", function (req, res) {
  res.send("<h1>Hello World!</h1>");
}); //localhost:3000/

app.listen(3000);
```

> Exporess get 메서드로 클라이언트의 요청을 분기로 처리하지 않고, 구조적으로 편리하게 사용할 수 있다.
