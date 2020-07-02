# what is git?
Git은 리누스 토발즈가 리눅스의 소스 코드를 관리하기 위해 만든 버전 관리 및 협업용 프로그램
## 디렉토리
`프로젝트 디렉토리` - 버전 관리 시작하는 폴더를 의미한다. `git init`을 한 폴더라고 생각하면 된다.   
`.git` 폴더가 있다면, 프로젝트 디렉토리라고 생각하면 된다.   
    
`.git 디렉토리` == `레포지토리`   

1. working directory   
  가) working directory는 작업을 하는 프로젝트 디렉토리
2. staging area   
  나) staging area는 git add를 한 파일들이 존재하는 영역
3. repository(`.git folder`)   
  다) working directory의 변경 이력들이 저장되어 있는 영역, 커밋되는 영역
## add
  git add 취소하는 방법 > `git reset file`
## 커밋
  `하나의 버전으로 남기고 싶을 때 저장하는 것`이라고 생각하면 된다.   
  Commit 에 필요한 것 > `이름` `이메일` `커밋메시지(커밋에 대한 정보)`   
  root-commit == 첫번째 커밋   
  `git commit (-m없이 하기)` 커밋 메시지를 여러 줄로 만들 수 있다. 저장방법은 Esc키 (i를 누르면 입력모드) > :wq + Enter   
  여러줄로 할 경우 커밋 메시지의 제목과 상세 설명 사이에는 한 줄을 비워두면 좋다.
### 커밋 수정하기
  `git add 후 git commit --amend `  
  
  

## 상태
일단 Git에서 파일들은 크게 다음 2가지 상태를 가집니다.
1. Untracked 상태   
2. Tracked 상태  
그리고 Tracked 상태는 다시 아래와 같은 3가지 상태로 나눌 수 있구요. 
1. Staged 상태   
2. Unmodified 상태   
3. Modified 상태   

## 명령어
1. `mkdir 이름` 
2. `ls -al`
3. `cd` 폴더 들어갈 시에는 `cd 폴더/` 나갈 시에는 `cd ..`
4. `git add .`   `git add *
  ```폴더 올리는 방법 git add 폴더/```
5. `git commit -m "COMMIT_MESSAGE"`
6. `git log`
6. `git remote -v`
7. `git config --list`
8. `git config --global user.name "USER-NAME"`
9. `git config --global user.email "USER@github.com"`
10. `git reset --hard commitID`
11. `git status
12. `touch 파일 이름` 파일 생성
13. `git rm file` 추가 기능이 있는 취소라고 생각하면 된다. 원격저장소에서 내리면서 unstaged.
14. `git help command name` or `man git-command name` _windows는 안될 수도 있음._   
_메뉴얼에서 나가고 싶으면 q를 누르면 된다 Ctrl + c 취소 됨._
15. `git push --set-upstream origin master` == `git push -u origin master`
16. `git clone git address`
17. `git log --pretty=oneline` _커밋 히스토리를 한줄로 깔끔하게 보겠다._
18. `git show commit ID` _어떤 파일이 어떻게 변했는지 보여준다._
19. `git config alias.history 'log --pretty=oneline' ` _이렇게 하면 앞으로_ `git history` _라고만 쳐도 된다.
20. `git diff commit id 2가지`

## invite a collaborator
아무나 Push 할 수는 없다. - 콜라보레이터 설정하기   
Settings - Manage access - PUBLIC REPOSITORY 밑 Invite a collaborator
