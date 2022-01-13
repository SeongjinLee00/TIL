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
