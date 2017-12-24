---
layout: post
title:  "Git - 변경 내용 확인(git diff) 및 파일 삭제(git rm)"
subtitle:   "Git help"
categories: development
tags: git
comments: true
---

Git에서 변경된 내용을 확인하는 방법과 파일을 삭제하는 법을 살펴보자.

## git diff 명령어

### git diff 와 git diff --staged 차이

`git diff` 명령어는 `working directory의 변경 내용`만 보여준다.  
즉, 아직 staged 되지 않은 파일들의 변경 사항을 확인 할 수 있다.

staged 된 파일들의 변경 사항을 보고 싶으면 `git diff --staged` 명령어를 사용하면 된다.

### git difftool - 다른 diff 툴 사용
`git difftool` 명령어를 쓰면 별도의 tool을 사용해서 diff 를 확인 할 수 있다.  
`git difftool --tool-help` 명령어를 통해 도움말을 얻을 수 있다.
 
diff tool 설정은 다음 3개의 lines을 입력함으로 해결 할 수 있다.  
출처 : [stackoverflow](https://stackoverflow.com/questions/6412516/configuring-diff-tool-with-gitconfig)
```
git config --global diff.tool tkdiff
git config --global merge.tool tkdiff
git config --global --add difftool.prompt false
```

처음 2 lines은 tkdiff 를 diff 와 merge 툴로 설정하는 명령어이고,  
3번째 line은 difftool 을 입력 할 때마다 command 창에서 묻는 질문을 없애는 기능이다.


## git rm 명령어

### staged 파일 삭제
`git rm -f [파일명]` 명령어는 staged 된 파일을 삭제 할 수 있게 해준다.  
-f 옵션은 실수로 데이터를 잃어버리는 일이 발생하지 않기 위해서다.

### 파일은 삭제하지 않고, tracking 만 무력화하기
`git rm --cached [파일명]` 명령어를 입력하면 tracking 만 무력화 할 수 있다.
> 이 기능은 .gitignore에 입력을 깜빡 했을 때 더욱 유용하다.
> 파일은 그대로 두고, tracking 만 무효화 할 수 있다.

### 여러 파일 삭제
`git rm log/\*.log` 명령어는 log 폴더에 있는 확장자가 log 인 모든 파일을 삭제하는 명령어이다.  
백슬래시(\\)가 추가로 있는 이유는 git이 shell 과는 별도로 파일 관리를 하기 때문이다.

`git rm \*~`는 ~로 끝나는 모든 파일을 삭제한다.
