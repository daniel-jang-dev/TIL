# 지옥에서 온 Git 02
> [(Git from the HELL)](https://www.youtube.com/playlist?list=PLuHgQVnccGMA8iwZwrGyNXCGy2LAAsTXk)

## branch

> branch 가 필요한 경우 example
> - client 에게 보여줄 작업이 필요할 때
> - 새로운 기능을 추가할 때
> - 테스트 작업을 할 때

    $git branch // 현재의 branch 확인
    * master // 기본 branch

    $git branch exp // exp라는 새로운 브랜치 생성
    $git branch
      exp
    * master

    $git checkout exp // exp branch 로 이동
    * exp
      master
      
    $git checkout -b exp // exp branch 생성 후 이동
    
> 모든 브랜치 비교해보기

    $git log --branches --decorate  --graph --oneline // 모든 브랜치 트리를 간략하게 보여줌

    $git log a..b // a에는 없고 b에는 있는 commit 들을 보여줌
    $git log a..b -p // "a에는 없고 b에는 있는" commit 및 파일 내용을 보여줌

    $git diff a..b // a와 b의 다른 점을 비교해서 보여줌

> 브랜치 병합하기 (exp => master)

    $git branch master // master로 이동
    $git merge exp // exp를 master로 병합

> 브랜치 지우기

    $git branch -d exp


> 작업 도중 다른 브랜치로 이동해야 하는 경우 
> (작업이 아직 끝나지 않아서 commit 할 수 없는데, 그대로 두면 다른 브랜치에도 영향을 미침)

	$git stash
