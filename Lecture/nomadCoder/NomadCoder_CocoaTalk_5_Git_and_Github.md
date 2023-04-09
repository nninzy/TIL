# 코코아톡 5. Git and Github

강의처: 노마드코더

기록 날짜: 2023/04/09

세줄 요약: git의 역할 / github의 역할 / repo 생성 및 github publish

주제: Git&Github

### git은 왜 필요한가

- 코드가 길거나, 팀 단위의 프로젝트, 큰 규모의 프로젝트에서는 파일의 히스토리를 알아야 한다. (처음에 뭘 작성했고, 이후에 뭘 변경했는지… 문제가 생기면 다시 그 전 상황으로 돌아가서 작업을 해야하기 때문)
- git은 코드를 다루는 text 파일 뿐만 아니라, 엑셀,이미지 파일 등의 다른 형식의 원하는 파일의 변경된 내용을 확인할 수 있게 한다.
← git 시스템은 파일을 binary format(이진수)으로 인식하기 때문

> **git은 파일을 계속 추적 (Tracking)하면서
파일의 버전(변경내용, 히스토리)을 관리할 수 있다.
⇒ version control system**
> 
- git 설치 ⇒ git-scm.com에서 본인 컴퓨터 사양에 맞는 버전 다운로드받기

### github은 왜 필요한가

파일의 변경 내용 (파일 내역과 파일들)을 업로드하는 공간

- github 사용 방법 ⇒ github 웹사이트에 들어가서 회원가입 또는 로그인
- github **repository**
    
    = 내 코드가 살고 있는 곳. (코드의 변경 내역과 히스토리를 갖고 있는 폴더)
    
    = 컴퓨터의 디렉토리를 복사한 것과 같은 형태를 가졌다.
    
    = 각 파일에는 history를 확인할 수 있다.
    
    히스토리에는 어떤 기록인지를 확인할 수 있는 메시지와 날짜, 작성자에 관한 정보가 담겨있다.
    
    - commit = 시점.
    각 커밋에는 이전의 코드는 어땠는지, 현재의 코드는 어떻게 됐는지 보여준다.
    ⇒ **명확하게 뭐가 변경됐는지 직관적으로 볼 수 있음**
        
        ⇒ 문제가 생겼을 때 돌아갈 지점을 직관적으로 알 수 있음
        
    

### repository 생성하기

- repository를 생성하는 방법
    1. 로컬(컴퓨터)에서 폴더를 만든 뒤 해당 폴더를 github에 올리는 방식
    2. github 내에 repository 생성
        - repository 이름 설정 = 공백 없이 소문자 작성
        - repository 공개 여부 = 공개되는 정보가 있는게 아닌 이상 private로 하는 것은 권장하지 않음
        (포트폴리오로 활용할 수 있고, 코드에 문제가 생길 경우 타인이 알려줄 수도 있음)
        public을 open source라고 한다.
        - 기타 파일 자동 생성 여부 = readme 파일, .gitignore 파일, license 등
- README.md
    
    모든 git repository가 갖고 있어야 하는 파일
    

- github desktop
    
    github이 어떻게 작동되는지 잘 보여주는 프로그램
    
    - clone a repository from the internet
        
        = github 사이트에 있는 파일 중 로컬에 내려받아 연결할 레포 선택 후 clone 가능
        
        = clone 파일 위치 (경로) 역시 변경 가능
            VS code에서도 폴더를 열어야 하기에 찾기 쉬운 위치에 생성할 것.
        
    - commit 생성하기
        
        = github에 올리고 싶은 파일, 한번에 묶어서 하나의 버전으로 만들 파일 선택 후 commit (repository의 버전 저장 시점) 설정하기
        
        = commit은 업로드하기 위해서 반드시 commit의 title (=commit messege)를 입력해야함. description은 필수적이지 않음.
        commit 시점에 무엇을 했는지에 대한 내용이 담겨 있어야 함
        
    - publish (github 사이트로 게시하는 과정)
        
        = 상단에 있는 publish branch를 눌러 pushing to origin 상태를 확인
        = commit이 git 뿐만 아니라 github에도 바뀌었음을 알려주는 과정
        

<aside>
👊 작업 (변경 또는 생성) ~ github 업로드까지의 과정

1. 파일 변경 후 저장 ⇒ **파일 저장**
2. @github_desktop. 변경 파일 체크 ⇒ **파일 선택**
3. commit 타이틀 작성 ⇒ **commit title 입력**
4. commit 버튼 클릭 ⇒ **commit**
5. 상단 바 중 publish branch 눌러 github에 업로드 ⇒ **push**
</aside>