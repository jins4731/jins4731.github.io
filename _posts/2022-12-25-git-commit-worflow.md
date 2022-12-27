---
title: git commit workflow
author: jins4731
date: 2022-12-25 23:12:00 +0900
categories: [Git, Git 정리]
tags: [Git]
pin: true
---

# git commit workflow

## 1. working directory

프로젝트의 작업공간
**_git add_** 명령어로 **staging area** 에 파일들을 추가할 수 있다.

```Bash
git add
```

> working directory 에서 **modified 파일**만 staging area 로 옮길 수 있다.

## 2. staging area

workindg directory 에서 commit 할 파일들을 모아놓은 저장소
**_git commit_** 명령어로 Repository에 파일들을 추가할 수 있다.

```Bash
git commit
```

**_git rm --cached_** 명령어로 staging area에 있는 파일들을 working directory로 되돌릴 수 있다.

```Bash
git rm --cached
```

## 3. Repository

staging area 에서 commit한 파일들이 모여있는 저장소
**_git push_** 명령어로 **로컬 Repository** 에서 **원격 Repository**로 저장할 수 있다.

```Bash
git push
```

---

# git file status

## **1. working directory** file status

- **untracked**: **_git_** 에서 버전관리를 하고 있지 않아 추적하지 못하는 파일(신규 파일)
- **tracked**: git의 버전관리 파일
  - unmodified: staging area에 있는 수정되지 않은 파일
  - modified: staging area 에 있는 수정된 파일

## **2. staging area** file status

- **staged**: staging area 에 반영된 파일
