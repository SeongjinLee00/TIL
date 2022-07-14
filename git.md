[TOC]



## Git 입문

Git = 분산 버전 관리 시스템

git init 으로 활성화

git add . 스테이지에 올리기

git commit -m "commit message" 커밋하기

git status 상태보기

working directory -> 내가 작업하고 있는 실제 디렉토리

staging area -> 커밋으로 남기고 싶은, 특정 버전으로 관리하고 싶은 파일이 있는 곳

repository -> 커밋들이 저장되는 곳

git config user.name

git config user.email

git log

git config --list

git clone {remote_repo}

git pull

github, git연동 최초 1번 clone, 이후 push,pull 주고받고 반복

git remote add 별명(관례상 origin) {remote_repo}

git push -u 별명(관례상 origin) master

## 간단한 Unix/Linux 명령어

현재 위치의 폴더, 파일 목록보기 ls

현재 위치 이동하기 cd path

상위 폴더로 이동 cd ..

폴더생성 mkdir name

파일생성 touch name

삭제하기 rm name

​				rm -r name

깃배시 디폴트 위치 ~ == C:\users\kys>



## 0114 수업내용

git init 로컬 레포지토리 생성

git status 현재 레포지토리 상태

git add Staging Area로 올림

git config user.email

git config user.name

git commit -m ""

git log

git remote add origin {}

git push -u origin master(처음 푸시할때만)

git pull

git clone {}



**push 전에는 pull이 있다**



Python Chatbot 맛보기





## Git branch

git branch : 브랜치 목록 확인

git branch 브랜치이름 : 새로운 브랜치 생성

git branch -d 브랜치이름 : 특정 브랜치 삭제(병합된 브랜치만)

git branch -D 브랜치이름 : 병합 안되어있어도 삭제가능

git branch 브랜치이름 : 다른 브랜치로 이동



git log --oneline 라고만 치면 현재 브랜치의 로그를 보여줌

모두 보고싶으면 git log --all --oneline

가지를 보고싶으면 git log --all --oneline --graph



git switch 브랜치이름 : 다른 브랜치로 이동

git switch -c 브랜치이름 : 새로 생성과 동시에 이동



git merge 브랜치이름

merge 하기 전에 합치려고 하는(주로 master) 브랜치로 switch해야함

merge가 된 브랜치는 역할이 끝났으니깐 삭제

1. fast-forward : 기존 가지에서 나아간게 없는 경우
2. 3-way merge : 일반적인 상황
3. merge conflict : 서로 다른 브랜치에서 같은 파일의 같은 라인을 수정한 경우
   - 이 경우 수정하고 그냥 git commit 하면 됨
   - vim editor에서 esc : wq



## TIL_0406

git branch {name} : 생성

git checkout {name} : 이동

git checkout -b {name} : 브랜치 생성하며 이동(귀찮은 사람들을 위해)

git branch : 브랜치 목록

git branch -d {name} : 브랜치 삭제



fast forward merge : 가리키던 포인터를 앞으로 땡기는거

merge commit case : 진짜 합치는거

 
