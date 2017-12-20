# git-command
깃 명령어 공략집  
자주는 아니지만 간간히 사용되는 명령어를 기록해서 명령어 퍼즐조각들을 맞춰보자.
[마크다운 문법](https://gist.github.com/ihoneymon/652be052a0727ad59601)

## config
$ git config --list  
$ git config --global user.name "H.Ban"  
$ git config --global user.email haxlys@gmail.com

## branch
**브랜치 목록과 마지막 커밋메세지도 보여준다**  
$ git branch -v  

**현재 위치한 branch와 merge된 or merge되지 않은 branch 목록**  
$ git branch --merged  
$ git branch --no-merged

**원격서버 branch 삭제**  
$ git push origin --delete *branch명*  
**로컬 branch 삭제**  
$ git branch -d *branch명*  

**리모트 서버의 모든 branch를 로컬로 받아서 로컬 branch와 비교하고 싶을 때**  
$ git fetch --all; git branch -vv  
ahead는 로컬의 앞서가는 commit 갯수, behind는 리모트에서 받지 못한 commit 갯수
