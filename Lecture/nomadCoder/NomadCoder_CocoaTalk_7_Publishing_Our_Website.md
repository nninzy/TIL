# 코코아톡 7. Publishing Our Website

강의처: 노마드코더

기록 날짜: 2023/04/18 → 2023/04/19

세줄 요약: github.io 만드는 방법 (with gh-pages branch)

주제: Git&Github

## Publish 전 배워야 하는 것들

### git branch

- 코드들의 평행세계.
- master branch에는 stable한 (잘 작동하는 것으로 어느정도 검증이 된) code를 올린다.
    
    실험하거나 새로운 기능을 추가할 때 branch를 제작한다.
    (똑같은 커밋에서부터 시작. 다른 설정이 들어가는 것)
    
    commit을 기반으로 이전 단계로 돌릴 수 있음
    
    파일 하나에 버전을 여러개로 둘 수 있음
    
- branch는 다시 master에 merge될 수 있다. (수정한 부분이 master와 겹치면 안된다. 충돌 X)
- 특수한 git branch **`gh-pages`**에서는 작업한 내용을 publish할 수 있다.
Static hosing = 자신의 static website를 무료로 업로드할 수 있고 공짜 URL을 제공
Static Website = HTML, CSS, JS만 갖고 있는 것 (FE 파트) Back-end 파트는 제공 X

### gh-pages

- 웹사이트 publish에 필요한 것. 반드시 해당 이름 그대로 입력해야함
    
    또한 public 레포여야 함.
    
- gh-pages branch 생성 후 publish branch를 눌러서 온라인 원격저장소에 branch 업데이트
- environment의 Deployment에서 view deployment 누르면 작업한 화면 웹 사이트로 보여짐
.com의 형태는 아니고 io의 형태지만 배포 가능함

### github 페이지 수정, 업데이트하기

1. **`master branch`**에서 **`작업 & 커밋`** (gh-pages 아님, 제일 기본적인 branch에서)
    
    모든 수정은 master에서 진행하며 commit 역시 master에서 진행함
    
2. **`gh-pages branch`**에도 update 필요 ⇒ 상단 카테고리 branch > `Update` from master 클릭
    
    Successfully merged master into gh-pages 알림 확인, gh-pages 내 commit 업데이트 확인
    
3. gh-pages branch에서 **`push`** origin 버튼 클릭 ⇒ github.it 업로드 확인
    
    Deployment에서 view deploy 버튼 클릭 시 업데이트 상황 확인 가능
    
    (곧바로 반영은 안될 수 있음, 약간의 시간 차 두고 확인하기)