# TIL
## GIT
Commit은 변경된 파일들을 저장하는 행위(버전)

git의 영역에는 Working Dirctory, Staging Area, Repository가 있다.

### git의 동작
git의 버전 관리를 시작할 디렉토리에서 
```git
git init
```

변경사항이 있는 파일을 staging area에 추가
```git
git add
```

staging area에 있는 파일들을 저장소에 기록
```git
git commit
```

단계별 파일 상태 확인
```git
git status
```

단, Commit history는
```git
git log
```

### 발생한 문제 및 해결
1. a.txt를 만들고 commit 생성, b.txt를 만들고 commit 생성하는 실습에서 둘을 동시에 add하고 원하는 것만 commit하면 된다고 생각하고 진행

    하지만 둘다 staging하면 둘다 commit이 되어버림, 만약에 둘다 staging했다면 staging down을 해줘야함 
    ```git
    git restore --staged <파일명>
    ```
2. desktop 경로에 git init을 해버려서 하위 폴더들의 저장소를 인식하지 못하는 문제가 발생해버림

    폴더 내의 ...을 누르고 -> 보기 -> 숨김파일 : 숨김 파일, 폴더 및 드라이브 표시 -> .git파일을 삭제함으로써 문제 해결

    만약에 맥에서 다음과 같은 문제가 발생 했다면?
    : mac도 동일하나 바탕화면에서 cmd + shift + .로 숨김파일들이 드러나게 하면 됨

### Remote Repoitory
원격 저장소로써 협업하고 코드를 공유할 수 있는 저장 공간임

- 로컬 저장소에 원격 저장소 추가
    ```git
    git remote add origin remote_repo_url
    ```
    orgin은 별칭으로써 첫 별칭은 orgin을 사용하는 것이 관행

    remote가 잘 되었는지는 다음과 같이 확인
    ```git
    git remote -v
    ```

- 원격 저장소에 commit 목록 업로드
```git
git push origin master
```

- 원격 저장소에 commit 목록 다운로드

    왜 push와 clone 두 가지인가?

    clone(복제 : 깃헙에 있던 커밋 전체를 다운 받음), pull(변경사항 만큼만 받는다)

- 만약 원격 저장소를 잘 못 등록했다면?
    ```git
    git remote rm <remote_name>

- gitignore
  
    git에서 특정 파일이나 디렉토리를 추적하지 않도록 설정

    데이터베이스 같은 경우 개인정보 등 민감한 정보가 있어서 git이 무시하도록 해야하는데 그것이 gitignore임

    한번이라도 버전관리(커밋) 받았다면 gitignore가 먹히지 않음. 따라서 gitignore는 가장 처음에 하는 것이 가장 좋음. 

    .gitignore 파일 생성하면 되고, 확장자는 없음

    - 자동으로 ignore 해주는 사이트[https://www.toptal.com/developers/gitignore/]

### git branch

작업 공간을 나누어 독립적으로 작업할 수 있도록 도와주는 GIT의 도구. 예를 들어 로그인, 게시판 등에 대해서 나누어서 브랜치를 개발

master(main) 브랜치는 저장소의 초기 상태. 다른 브랜치가 파생되는 기준점으로 사용되며, 다른 브랜치에서 작업 후 master 브랜치에 병합.

- 브랜치 명령어
    - 브랜치 목록 확인
        ```git
        git brnch
        ```

    - 원격 저장소 브랜치 목록 확인
        ```git
        git branch -r
        ```
    - 새 브랜치 생성
        ```git
        git branch <브랜치 이름>
    - 브랜치 삭제
        ```git
        git branch -d(병합된 브랜치만)/-D
    - 다른 브랜치로 전환
        ```git
        git siwtch <다른 브랜치>
    - 새 브랜치 생성 후 전환
        ```git
        git sitch -c <브랜치 이름>

- head
  
  우리가 보고 있는 위치

  진행 방향과는 다른 화살표(이유는 의존의 방향이기 때문)

- git merge
  
  병합 전 나의 위치 확인과 양쪽의 최신 상채의 커밋 상태 유지를 확인 할 것

  - fast-forward merge
    
    병합 대신 대상 브랜치 상태로 이동시키는 작업

  - 3-way merge
    

    각각의 최신, 각각의 공통 조상 그래서 3개의 커밋을 본다해서 3way

- merge conflict
  
  병합하고자 하는 두 브랜치가 동일한 파일의 동일한 부분에서 변경된 후 병합 시 충돌 발생

  둘중에 하나 수정하라 / 위에는 수신영역, 아래는 병합 영역

- 작업 중 VIM 에디터가 나타날 경우
  
  - 입력모드(텍스트 입력) 
    i를 누르면 됨

  - 명령모드 
    shift + ; 누르면 됨

    저장은 w, 종료는 q 

    wq 누르면 됨