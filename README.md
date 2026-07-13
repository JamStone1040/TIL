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