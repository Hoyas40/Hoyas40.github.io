---
layout: post
title:  "Git - 파일 무시하기 - .gitignore"
subtitle:   "Git ignore files"
categories: development
tags: git
comments: true
---

.gitingore 파일을 이용하면 Git 저장소에서 트래킹 하지 않을 (즉 무시 해야 하는) 파일들의 목록을 지정할 수 있다.

## Github 예제 파일들
GitHub에서 다양한 언어와 플랫폼( 예 : Visual Studio ) 에 대한 .gitignore 예제를 제공한다.  
[GitHub 링크](https://github.com/github/gitignore)

## 언제 .gitignore를 만들어야 하는가?
git 저장소를 만들었다면 그 직후에 바로 만드는 것이 좋다.  
commit 되지 말아야 할 파일들이 commit 되는 것을 막을 수 있다.


## .gitignore 의 패턴 규칙

.gitignore 파일에서 사용 할 수 있는 `패턴의 규칙`은 다음과 같다.
* \# 로 시작하는 라인은 주석에 해당한다. 따라서 무시된다.
* `GLOB`을 사용 할 수 있고 working tree의 sub folders에 적용된다.
* 슬래시 (/) 로 시작하면 sub-folder 들에 적용되지 않는다.
* 슬래시 (/) 로 끝나면 sub-folter에 적용된다.
* 느낌표 (!) 를 사용하면 패턴을 무효화 할 수 있다.

```
GLOB 패턴은 shell 에서 사용하는 정규 표현식의 간략화(simplified) 된 버전이다.
```

### 패턴 예제

간단한 규칙은 다음과 같다.
* \*(asterisk) 
  * 정규표현식 처럼 `0 개 이상의 문자`에 해당한다.
* [abc]
  * a, b, c 세 문자 중 하나에 해당한다.
* [0-9]
  * `0부터 9`의 문자에 해당
* ?
  *  `1 개의 문자`에 해당한다.
* \**
  *  하위 폴더( nested folder )
  *  즉, a/\*\*/z 는 a/z, a/b/z, a/b/c/z 등과 매칭된다.

```
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in the build/ directory
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```


