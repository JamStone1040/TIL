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

(git도 아마 메모 못한거 있는데 마저 메모하기)

---
## Python(0720 필기는 마저 필기하기)
\n

(0721 수업 내용)
### 함수 
재사용 가능한 코드 묶음

- 함수 구조
1. def 키워드로 시작
2. : 다음에 들여쓰기 된 부분이 body
3. Docstring(선택적)<br>
   함수 설명서<br>
&nbsp;&nbsp;&nbsp;&nbsp;"""이것은 두 수를 받아<br>
&nbsp;&nbsp;&nbsp;&nbsp;두 수의 합을 반환하는 함수입니다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;>>> make_sum(1,2)
&nbsp;&nbsp;&nbsp;&nbsp;3<br>
&nbsp;&nbsp;&nbsp;&nbsp;"""
4. return  
   함수의 실행을 종료하고, 결과를 호출 부분으로 반환
5. 함수의 이름과 소괄호를 활용해 호출  

- 매개변수와 인자
    - 매개변수
        <br> 함수를 정의할 때, 함수가 받을 값을 나타내는 변수
    - 인자 <br> 함수를 호출할 때, 실제로 전달되는 값

- 다양한 인자 종류
  - 위치인자
    - 함수 호출 시 인자의 위치에 따라 전달되는 인자
    - 위치 인자는 함수 호출 시 반드시 값을 전달해야 하며, 하나라도 사용하지 않을 시 실행 안됨
  - 기본 인자 값
    - 함수 정의에서 매개변수에 기본 값을 할당하는 것
    - 함수 호출 시 인자를 전달하지 않으면, 기본값이 매개변수에 할당됨
  - 키워드 인자
    - 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자
    - 매개변수와 인자를 일치시키지 않고, 특정 매개변수에 값을 할당할 수 있음
    - 인자의 순서는 중요하지 않으며, 인자의 이름을 명시하여 전달
    - 단, 호출시 키워드 인자는 위치 인자 뒤에 위치해야 함<br>
    ```python
    def greet(name, age): 
        print(f'안녕하세요, {name}님! {age}살이시군요.')

    greet(age=35, 'Dave') # 불가능
    greet('Dave', age=35) # 는 가능
    ```

  - 가변 인자
    - 정해지지 않은 개수의 인자를 처리하는 인자
    - 함수 정의 시 매개변수 앞에 '*'를 붙여 사용
    - 여러 개의 인자를 tuple로 처리
  - 가변 키워드 인자
    - 정해지지 않은 개수의 키워드 인자를 처리하는 인자
    - 함수 정의 시 매개변수 앞에 '**'를 붙여 사용
    - 여러 개의 인자를 dictionary로 묶어 처리

  - 함수 인자 권장 작성 순서(절대적 규칙은 아님)<br>위치 -> 기본 -> 가변 -> 가변 키워드

- 재귀 함수<br>함수 내부에서 자기 자신을 호출하는 함수
  - 1개 이상의 base case(종료되는 상황)이 존재하고, 수렴하도록 작성
  - 메모리 사용이 많으며, 종료 조건이 잘못되면 스택 오버플로우 에러가 발생할 수 있음

- 내장 함수<br>파이썬에 기본적으로 내장된 함수

- 함수와 Scope<br> 함수는 코드 내부에 local scope를 생성하며, 그 외 공간인 global scope로 구분
  - 변수 수명 주기
    - built-in scope<br>파이썬이 실행된 이후부터 영원히 유지
    - global scope<br>모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
    - local scope<br>함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지
  - 이름 검색 규칙
    - 파이썬에서 사용되는 이름(식별자)들은 특정한 이름공간(namespace)에 저장되어 있음
    - 아래와 같은 순서로 이름을 찾아 나가며, LEGB Rule이라고 부름<br>
      1. Local scope
      2. Enclosed scope
      3. Global scope
      4. Built-in-scope
    - 이름이 없으면 찾아 나가는 순서이며, 없으면 더 바깥에서 찾아옴
    - 함수 내에서는 바깥 영역에서 찾아올 수 있지만 반대의 경우는 안됨(로컬은 바깥 쪽은 되지만 안쪽은 안됨)<br>

        ```python
        X = 'G'
        y = 'G'

        def outer_func():
        X = 'E'
        y = 'E'

        def inner_func(y):
        Z = 'L'
        print(x, y, z) # EPL

        inner_func('P')
        print(x, y) # E E

        outer_func()
        print(x, y) # G G
        ```

- global 키워드
  - 변수의 스코프를 전역 범위로 지정하기 위해 사용
  - 일반적으로 함수 내에서 전역 변수를 수정하려는 경우에 사용
  - 주의사항
    - global 키워드 선언 전에 참조 불가
    - 매개변수에는 global 키워드 사용 불가

- Packing & Unpacking
  - 패킹
    - 여러 개의 데이터를 하나의 컬렉션으로 모아 담는 과정
    - 튜플로 묶임
    - 함수 매개변수 작성시 '*'을 활용해서 남는 위치 인자들을 튜플로 묶을 수 있음
    - 함수 매개변수 작성시 '**'을 활용해서 남는 위치 인자들을 딕셔너리로 묶을 수 있음
  - 언패킹
    - 컬렉션에 담겨있는 데이터들을 개별 요소로 펼펴 놓는 과정
    - 리스트나 튜플 앞에 *를 붙여 각 요소를 함수의 개별 위치 인자로 전달(함수 인자 전달)
    - 딕셔너리 앞에 **를 붙여 딕셔너리 형태의 키워드 인자로 전달(딕셔너리 -> 함수 키워드 인자), key 이름이 매개변수 이름과 같아야 함

- 참고
  - 함수의 return, 반환의 원칙
    - 파이썬 함수는 언제나 단 하나의 값(객체)만 반환할 수 있음
    - 여러 값을 반환하는 경우에도 하나의 튜플로 패킹하여 반환함
  - 람다 표현식
    - 익명 함수를 만드는데 사용됨(일회용도로 쓰고 싶어서)<br>
  
    ```python
    def addition(x, y):
        return x + y
    # 람다 표현식
    lambda x, y : x + y
    ```