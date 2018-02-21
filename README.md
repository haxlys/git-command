# git-command
깃 명령어 공략집  
자주는 아니지만 간간히 사용되는 명령어를 기록해서 명령어 퍼즐조각들을 맞춰보자.  
[마크다운 문법](https://gist.github.com/ihoneymon/652be052a0727ad59601)  

## local branch와 track remote branch
https://www.git-tower.com/learn/git/faq/track-remote-upstream-branch  
local 컴퓨터에는 remote branch와 local branch가 함께 있다.  
git fetch 실행하면 local 컴퓨터에 있는 remote branch 를 최신화하게 된다.  
local branch를 최신화하고 싶다면 git merge 명령어를 통해서 git fetch로 가져온 local 컴퓨터에 있는 remote branch로 부터 소스를 가져와 local branch와 병합을 한다.  
git pull하면 직접적으로 원격서버와 통신하여 다이렉트로 병합을 시도하는것 처럼 보이지만 내부적으로는 이런 시스템으로 병합을 하게 된다.  

merge는 결국 세 가지 경우가 있다.  
해당 branch가 추적(tracked)하는 remote branch와 병합 -> git pull *remote명 현재branch명*  
다른 local branch와 병합 -> git merge *branch명*  
다른 remote branch와 병합 -> git pull *remote명 branch명*  

첫번째와 세번째 경우는 똑같다고 할 수 있다.  
여기서 첫번째 경우에 더 간단히 git pull 만으로 remote branch와 병합할 수 있는 방법은 upstream branch 를 설정해주는 것이다. 

### branch 생성시 기존에 있던 remote branch를 upstream branch로 설정하는 경우
$ git checkout -b *branch remote명/branch명* -> local branch명을 upstream branch와 이름을 다르게 할 필요가 있을 때 사용.  
$ git checkout --track *remote명/branch명* -> remote branch이름으로 local branch가 생성된다.
### 현재 local branch에 upstream branch를 할당하기
$ git branch -u *remote명/branch명*  
### upstream branch가 없는 현재 local branch를 push와 함께 upstream branch 할당
$ git push -u *remote명 branch명*  

위 명령어를 통해서 upstream branch를 설정했다면 git pull, git push 명령어 만으로 설정된 remote branch로 push pull을 할 수 있다.

## config
$ git config --list  
$ git config --global user.name "H.Ban"  
$ git config --global user.email haxlys@gmail.com

## branch
**브랜치 목록과 마지막 커밋메세지 확인**  
$ git branch -v  
**-v 옵션 내용과 더불어 upstream branch도 보여줌**  
$ git branch -vv  

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

**remote 정보 가져오기**
git remote show *리모트 저장소 이름*

## add
모든 변경, 삭제, 새로운 파일을 stage에 올림  
$ git add -A  
삭제를 제외한 변경, 새로운 파일을 stage에 올림  
$ git add .   
새로운 파일을 제외한 변경, 삭제된 파일을 stage에 올림  
$ git add -u
