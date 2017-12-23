---
layout: post
title:  "Git 최초 Setup 방법 및 도움말"
subtitle:   "Git Setup and help"
categories: development
tags: git
comments: true
---

Git 시작 시 Setup 하는 법을 알아보자.

## Git 시작 시 Setup 방법

### git config 명령어

git config 명령어는 사용자로 하여금 git의 `환경 변수를 설정` 할 수 있도록 도와준다.  
git의 환경 변수들은 `3 개의 파일`에 저장되어 있다.

system              |  global                              | project
:------------:      |:---:                                 |      :----:
/etc/gitconfig      | ~/.gitconfig or ~/.config/git/config | .git/config
모든 사용자            | 해당 사용자                             | 해당 프로젝트
git config --system | git config --global                  | git config ( in the project )

같은 변수가 존재한다면, system < global < project 의 `우선 순위`를 가지게 된다.

### 사용자 등록

git 설치 후 가장 먼저 해야 할 일은 `사용자인 정보`를 기록하는 것이다.  
아래 command는 `--global` 옵션으로 저장하기에 딱 한 번만 실행하면 된다.
```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

### editor 설정
`메시지 입력` 등을 위해 git이 사용 할 editor 를 설정 할 수 있다.
해당 환경 변수가 입력되지 않을 경우, `시스템 editor`를 사용하게 된다.
```
$ git config --global core.editor vim
```

### 현재 설정 확인

```
$ git config --list

user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...
```

같은 key 가 반복될 수 있는데, git config --list 는 3 파일에 들어 있는 값들을 모두 보여주기 때문이다.