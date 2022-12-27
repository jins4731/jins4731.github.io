---
title: git difftool 설정
author: jins4731
date: 2022-12-25 23:44:00 +0900
categories: [Git, Git 정리]
tags: [Git]
pin: true
---

# git difftool 설정 (VS Code)

## git config

```bash
git config --global -e
```

## .gitconfig 설정

```
[diff]

tool = vscode

[difftool "vscode"]

cmd = code --wait --diff $LOCAL $REMOTE
```

## git difftool

```bash
git difftool
git difftool --staged
```
