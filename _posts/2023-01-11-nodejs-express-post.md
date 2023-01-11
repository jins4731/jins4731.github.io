---
title: Nodejs-Express 사용자 데이터 구문 분석
author: jins4731
date: 2023-01-11 23:00:00 +0900
categories: [Backend, Nodejs]
tags: [Nodejs]
pin: true
---

# Express 사용자 데이터 구문 분석

## Express post 메서드

```javascript
const express = require("express");
const app = express();

//들어오는 모든 요청에서 실행되어야 하는 추가 핸들러를 작성할 수 있다.
// 이러한 하나 이상의 유형의 요청에 적용되는 일반 핸들러 함수를 일반적으로 미들웨어 함수라고 부른다.
app.use(express.urlencoded({ extended: false })); //바디 파서를 설정하는 메서드

app.get("/currenttime", function (req, res) {
  res.send("<h1>" + new Date().toISOString() + "</h1>");
}); //localhost:3000/currenttime

app.get("/", function (req, res) {
  res.send(
    '<form action="/store-user" method="POST"><label>Yout Name</label><input type="text" name="username"><button>Submit</button></form>'
  );
}); //localhost:3000/

app.post("/store-user", function (req, res) {
  const userName = req.body.username;
  res.send("<h1>Username stored!</h1>");
});

app.listen(3000);
```

> app.use() 메서드로 request 요청 데이터를 post 메서드 에서 처리하기 전에 javascript 에서 사용할 수 있는 데이터로 변환 해준다. 해당 메서드를 일반적으로 미들웨어 함수라고 부른다.

## 서버 파일에 데이터 저장하기

```javascript
const fs = require("fs");
const path = require("path");

const express = require("express");
const app = express();
//들어오는 모든 요청에서 실행되어야 하는 추가 핸들러를 작성할 수 있다.
// 이러한 하나 이상의 유형의 요청에 적용되는 일반 핸들러 함수를 일반적으로 미들웨어 함수라고 부른다.
app.use(express.urlencoded({ extended: false })); //바디 파서를 설정하는 메서드

app.get("/currenttime", function (req, res) {
  res.send("<h1>" + new Date().toISOString() + "</h1>");
}); //localhost:3000/currenttime

app.get("/", function (req, res) {
  res.send(
    '<form action="/store-user" method="POST"><label>Yout Name</label><input type="text" name="username"><button>Submit</button></form>'
  );
}); //localhost:3000/

app.post("/store-user", function (req, res) {
  const userName = req.body.username;
  const filePath = path.join(__dirname, "data", "users.json"); //text 로 읽힘
  const fileData = fs.readFileSync(filePath);
  const existingUsers = JSON.parse(fileData);

  existingUsers.push(userName);
  fs.writeFileSync(filePath, JSON.stringify(existingUsers));
  res.send("<h1>Username stored!</h1>");
});

app.listen(3000);
```

> 서버에 파일을 저장하기 위해서 fs 와 path 패키지를 사용한다.
> dirname 은 절대경로를 나타내는 자바스크립트 변수이다.
> JSON 을 이용하여 저장할 데이터와 가지고 온 데이터를 파싱한다.
