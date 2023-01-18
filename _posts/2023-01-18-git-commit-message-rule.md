---
title: git commit message rule
author: jins4731
date: 2023-01-18 19:14:00 +0900
categories: [Git, Git 정리]
tags: [Git]
pin: true
---

# Git Commit message 규칙

## Commit message Format

Each commit message consists of a **header**, a **body** and a **footer**. The header has a special format that includes a **type**, a **scope** and a **subject**:

## Commit message seven rule

1. 제목과 본물을 한 줄 **띄어** 구분
2. 제목은 **50자** 이내
3. 제목 첫 글자는 **대문자**
4. 제목 끝에 **마침표는 쓰지 않는다.**
5. 제목은 **명령문**으로, **과거형으로 쓰지 않는다.**
6. 본문의 각 행은 **72자** 이내 (줄바꿈 사용)
7. 본문은 어떻게 보다 **무엇을**, **왜** 에 대하여 설명

## Commit message structure

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

### type

- feat: A new feature.
- fix: A bug fix.
- build: 빌드 관련 파일 수정에 대한 커밋
- chore: Changes to the build process or auxiliary tools and libraries such as documentation generation. `ex).gitignore`
- ci: CI 관련 설정 수정
- perf: code change that improves performance.
- docs: Documentation only changes.
- style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
- refactor: A code change that neither fixes a bug nor adds a feature.
- test: Adding missing tests.

### scope

The scope is optional and could be anything specifying place of the commit change. For example `nsis`, `mac`, `linux`, etc...

### subject

type 과 함께 헤더를 구성한다. 예를 들어, 로그인 API 를 추가했다면, 다음과 같이 구성할 수 있다.
`ex) feat: Add login api`

The subject contains succinct description of the change:

- use the imperative, present tense: `change` not `changed` nor `changes`,
- don't capitalize first letter,
- no dot (.) at the end.

### body

헤더로 표현이 가능하다면 생략이 가능하다.
헤더로 표현할 수 없는 상세한 내용을 적는다.

### footer

어떤한 이슈에 대한 comit 인지 issue number 를 포함한다.
예를 들어 특정 이슈를 참조하려면 close#1233 과 같이 추가한다.
close는 이슈를 참조하면서 main 브랜치로 푸시될 때 이슈를 닫는다.

### 참고

A detailed explanation can be found in this [document](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#).
