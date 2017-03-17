# 지옥에서 온 Git 01
> [(Git from the HELL)](https://www.youtube.com/playlist?list=PLuHgQVnccGMA8iwZwrGyNXCGy2LAAsTXk)

### 1. 수업 소개

CVS -> SVN -> GIT

일반인 버전: Dropbox, Google Drive 

### 2. Git 설치

[Git install page](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
/ 
[Download Git for Windows](https://git-scm.com/download/win)

Git Bash 에서 Git version 확인

    $git --version
    v2.12.0.windosws.1

### 3. Code on Web
> [Codeonweb](https://www.codeonweb.com/dashboard/) 실습 선택 후 언어를 Git 선택

### 4. git init 

    $git init // create an empty Git repo or reinitialize an existing one
    
    $git status // status 확인
    @git add * // 모든 파일 추가 (Stage area: 커밋 대기 상태)

    $git config --global user.name daniel
    $git config --global user.email daniel.jang@programmer.net
    // 유저 네임/이메일 설정

    $git commit -m "message" // 버전 생성 + 메시지
    $git log // 로그 기록 확인

> 흐름
>  - 파일 생성/변경
>  - git status // stage 에 올리기 전 status 확인
>  - git diff // 이전 commit 후 변경사항 확인
>  - git add 파일
>  - git commit -m "msg"
>  - 또는 git commit -am "msg"// 변경/삭제된 모든 파일이 add 됨. 단, 새 파일은 add 안 됨

### 5. 변경 사항 확인하기 (log / diff)

    $git log // show the commit history for the currently active branch
    $git log -p // 각각의 commit 에서 변경된 사항 / 차이점 확인

    $git diff aaa..bbb // commit 된 상태의 aaa 와 bbb 의 차이점 확인
    $git diff // 스테이지에 올라간 부분 / 그렇지 않은 부분의 차이점 확인

### 6. 과거로 돌아가기 (reset)

    #git reset aaa --hard // aaa commit 상태로 돌아감(local 작업에 대해서만 reset / repo 는 리셋하지 말 것)


### 7. 기타

Git 에서 가장 빈번하게 사용되는 명령어
> commit, push, pull, clone, checkout, add, branch, log, diff, fetch, merge, init
