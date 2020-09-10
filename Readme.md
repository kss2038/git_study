### Git 을 커밋한 후에 수정이 필요할 경우
git log --onefile : 현재 커밋된 정보를 확인  
git reset HEAD^ : 커밋한 정보를 리셋    
git log --onefile : 위에서 리셋된 후 커밋을 확인  
모두 리셋되었으면 다시 add * 후 커밋하면 된다.

### master 의 변경된 사항을 local 로 불러오는 방법  ###
git pull origin master

### git 실행 및 기초 명령어 ###
바탕화면 git bash 실행
```github
$ git config --list
$ git config user.name
$ git config --global user.name <github-name>
$ git config user.email
$ git config --global user.email <email>
$ git config # 한눈에 보기  
  cat ~/.gitconfig
```
### git Bash 에서 한글이 안될 때 ###
(참고) windows 에서 GitHub 에 한글이 깨질 때,
cmd > (chcp 65001) CMD 에 타이핑할 때는 괄호 제거해야 함

### git config 명령어 ###
git config --list | grep "user.name" # grep 은 필터링 하는 것으로 config 에서 user.name 

### 로컬 저장소 만들기 ###
```github
$ cd <work-dir>
$ git init
$ .gitignore 파일 작성 (서버 리파지토리에 업로드하기 싫은 파일 목록을 작성하는 용도; 다른 작업자와 함께 작업해야 하는 상황임을 )
$ git add --all (로컬 리파지토리인 .git 에 넣어줄 준비를 마친다는 의미; 아직 .git 으로 들어간 상황 아님)
$ git add <file명> 또는 git add . 또는 git add *
$ git commit -am "first commit message" 또는 git commit -m "first commit message" (이제서야 .git 로컬 리파지토리에 들어간 것)
$ git remote add origin <git-remote-url> # 서버 리파지토리와 로컬 리파지토리가 연결된다.
$ git push -u origin master # -u 는 최초 1회만 하면 됨; -u 의 뜻은 upload
$ git log
$ git status
```

### 이론 ###
branch 말고, main 줄기를 "origin master" 라고 부름 (즉 master branch) 
코드를 수정할 일이 생겼을 때, master branch 를 직접적으로 작업하기엔 백업이 없어서 위험하다.  
그래서 백업 개념의 branch 를 뽑아내어서 작업을 하고, 정상 작동 테스트까지 마친 후 master branch 로 merge 를 해야 한다는 것이다. \

```github
$ git commit -am "first commit github"
[master (root-commit) 84fbcf2] first commit github
 2 files changed, 4 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 hellopython.py
```
우리는 위의 코드를 통해서 master (root-commit) 인 master branch 에 직접적으로 commit 을 한 것이다.
```github
$ git branch # 현재 존재하는 branch 
```

master branch 의 내용이 변경되었는데도 먼저 pull 하지 않고, 로컬의 내용을 덮어 쓰려면 기본적으로 서버에서 reject 을 한다.
만약 무시하고 업로드하려면 `git push -fu origin master`를 입력하면 된다. (force 강제로 업로드 하라는 것)

### Git Branch ###
```github
$ git branch <branch-name> # branch 만들기
$ git branch # branch 전체 보기
$ git checkout <branch-name> # 전환
### 소스 수정 & add & commit ###
$ git push origin <branch-name>
$ git log
$ 다른동료폴더> git clone <git-remote-url> OR
  다른동료폴더> git pull
```

