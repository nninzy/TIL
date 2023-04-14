# 코코아톡 6-1. Cloning Time - 기본설정과 login 페이지 제작

강의처: 노마드코더
기록 날짜: 2023/04/09
세줄 요약: 기본 설정 (.gitignore / BEM / reset css / css file organize)과 login component (status-bar / header / form) 제작
작성 완료: Yes
주제: CSS, HTML

- 목차

> 코코아톡 클론코딩의 목표 = CSS 연습 (디자인 연습)
> 

### .gitignore

- 깃허브에 특정 파일을 업로드하고 싶지 않을 때, commit과 push에서 제외되는 파일들을 설정해주는 것
    
    git은 내 디렉토리에서 모든 파일을 참조할 수 있기에 DS store 나 비밀번호 등 깃허브에 공유되면 안될 것들도 공유될 수 있음
    
- 반드시 파일 네이밍은 `. + gitignore`이라고 해야함
    - 내부에는 무시하고 싶은 파일 이름을 넣으면 되며, 어떤 파일 이름이라도 쓸 수 있다.
    - 폴더를 넣고 싶다면 `/ + 폴더명`을 입력하면 된다.

## Login 페이지 만들기 = html 작업

### 작업 전 확인하기

- index.html 파일 화면 열기
- 오른쪽 하단 HTML과 Prettier의 작동 여부 확인

### 단축키

- `! + enter`
= HTML에 필요한 최소한의 코드를 만들어줌
- `alt + 마우스 클릭`
= 원하는 위치 여러곳에서 같이 입력 가능
- <head>에 `link:css` 입력

### index.html

- 대부분의 웹 서버는 디폴트로 index.html을 찾도록 설정되어 있음
- 영어에서 index는 첫번째라는 의미를 갖고 있기 때문

### **status-bar (상태바) 만들기**

1. div를 만들고 ~~id~~class=”status-bar” 입력
    
    ~~상태바는 한개의 HTML 내에서 한개만 존재하기에 id 속성을 사용~~
    
    CSS 작성 시 해당 요소가 id 였는지 class 였는지 헷갈리는 경우가 생기기에 class로 통일
    (모든 선택자에 동일하게 `.` 만 사용하면 혼동이 없으니까)
    
2. 상태바 내 구분되어 보이는 열 3개로 보임 ⇒ div.status-bar__column * 3 생성
⇒ 이런 클래스 명명 방식을 `BEM`이라고 한다.
CSS에서 선택자로 이용할 때 어떤 요소에 속한 것인지 빠르게 알 수 있도록하기 위함
부모와 자식 관계를 명시하면서 사용한다.
3. status-bar__column 항목에 <span> + <i> 아이콘 추가
아직 아이콘은 정하지 않았으니, `주석처리`로 일단 위치 체크만
    
    <aside>
    👊 **주석처리**
    
    개발자만 볼 수 있는 코드로, 브라우저는 주석처리된 부분을 그냥 지나간다.
    
    HTML 코드에서의 주석 처리는 `<!-- -->`으로 한다.
    
    CSS 코드에서의 주석 처리는 `/* */`으로 한다.
    
    </aside>
    

### header 만들기

1. title이라고 할 수 있는 부분 h1 tag, 설명이라고 할 수 있는 부분 p tag 이용
2. 많은 페이지에 header가 존재할 것이기에 header에 class를 이용해서 특정짓기
    
    ex. welcome-header
    
3. h1과 p에도 BEM 방식을 이용해서 class명을 입력한다.

### form 만들기

1. input 요소를 이용해서 내부 항목을 입력해준다.
    - Log in 버튼의 경우 <button> or <input type=”submit”> 이용
    - 계정찾기는 링크일 것이기에 a tag를 이용해 넣어준다.
        
        ⇒ form 안에 넣는 이유 = 
        
2. 과제 전체를 살펴봤을 때 form은 많으면 2번 정도 사용될 것이기에
class를 붙여주지 않는다.
    
    대신 id=”login-form”을 입력한다.
    
3. a tag는 웹 사이트를 만들면서 많이 사용될 것이기에,
이 페이지만을 위한 class나 id는 입력하지 않는다.

> html에서 BEM을 이용해 class명을 미리 입력하기 = 공간으로 구분되는 곳.
하위 요소는 pseudo selector 이용해서 접근
> 

### form의 중요한 속성 = action과 method

- action = 어떤 페이지로 데이터를 다른 페이지로 보내는 역할
- method = 2가지 방식 중 하나를 쓸 수 있음 (POST / GET)
    1. POST
        
        = 백엔드 서버에 정보를 전송하는 방식
        
        = 현재 우리가 프로젝트 업로드하는 방식에서는 POST 방식 작동 안함
        
    2. GET
        
        = URL에 포함되어도 상관없는 정보를 전송하는 방식
        
        = 검색 결과와 같은 요소들은 GET 방식을 많이 사용하고,
        password와 같은 보안이 중요한 요소는 GET 방식을 사용하면 안된다.
        

> 자세한 내용을 알고 싶다면 `[풀스택] 유튜브 클론코딩` 추천
> 

---

## Login 페이지 만들기 = CSS 작업

### index.html의 CSS를 넣어줄 styles.css (style.css라고 써도 ok)

1. index.html에 styles.css 위치 걸어주기
    
    `link:css` 입력 후 href만 알맞게 수정
    
    링크 잘 걸렸는지 background-color 주는 등의 방법으로 확인
    
    <aside>
    💡 이슈노트
    
    - 발생 상황 : css 파일 입력 시 / 를 누르고 키워드가 뜨는 부분부터 입력했더니 현재 위치를 브라우저가 인식하지 못함
    - 파일 참조는 절대 참조와 상대 참조가 있음
    상대 참조는 작업중인 현재 파일 위치를 기준으로 함
    </aside>
    
2. class는 공간의 역할을 하는 곳 (div, header 등에 있음)에 주로 명명한다.

### reset CSS (작업 전 없애야하는 설정 초기화)

- body elemet에 브라우저가 알아서 html에 적용시키는 스타일 등을 초기화하는 파일
대부분의 태그에 `margin` `padding` border: 0를 가진 파일
- 완전 처음부터 시작하고 싶을 때 사용
(브라우저에 상관없이 항상 동일한 사이트를 보이게 하는 용도)
- 사용 방법
    1. 구글 검색해 얻은 reset css 사이트 내 있는 css 설정을 모두 들고와 reset.css이라는 새로운 파일을 넣어 붙여넣는다.
        
        [Eric Meyer’s “Reset CSS” 2.0 | CSS Reset](https://cssdeck.com/blog/scripts/eric-meyer-reset-css/)
        
    2. style.css에 리셋 css를 import 한다.
        
        최상단 import를 입력하는 위치에 `**@import “reset.css”;**` 입력. 세미콜론 잊지말기
        
        (css에 import를 이용해서 연결해주는게 좋음. html에 link를 여러줄 만들어서 연결하는 것은 권장하지 않음)
        
    3. status-bar 등과 같은 다른 페이지에도 동일하게 적용되는 특정한 css를 비롯해 각 화면의 css 역시 별도의 파일을 만들고 style.css에 import 하는 방식을 추천
    
    > 코드를 먼저 대충 작성하고, 이후에 코드를 정리하는 작업을 진행할 예정
    > 

### BEM (Block Element Modifier)

- 많은 사람들이 적용시키는 규칙 중 하나 / 좀 더 쉽게 읽히는 CSS를 갖는 것
- 규칙
    - `.btn {}` ⇒ Bloock component / `컴포넌트 이름` 명시
    - `.btn--orange {}` ⇒ `컴포넌트명` + `--` + `바뀐 스타일 내용` 명시
    Modifier that changes the style of the block
    (컴포넌트 스타일에 변경된 사항이 있는 경우)
    - `.btn__price {}` ⇒ `컴포넌트명` + `__` + `자식요소` 명시
    Element that depends upon the block (컴포넌트에 속한 자식 관계의 요소 명시)
        
        ```html
        <a class="btn btn--big btn--orange" href="https://a.com">
        	<span class="btn__price">9900won</span>
        	<span class="btn__text">Subscribe</span>
        </a>
        ```
        
    - 클래스가 커질 수 있다는 단점이 있지만, 단점으로 여기는 사람들은 주로 입문자들
        
        > 프로들이 어떻게 하는지 알아보고 코드를 이해하려고 하는건 중요하다.
        > 

### 색상 컬러칩 CSS 파일 만들기

- variable.css 파일을 CSS 폴더 내에 만들고 style.css에 @import “variable.css”하기 (어차피 동일한 위치이기에 상대경로 추가 설정 필요 없음)
    
    > 반드시 import 할 것.
    > 
- variable.css에는 다음과 같이 설정하고, style.css에는 **`var(--yellow)`**를 속성값으로 입력
    
    ```css
    @variable.css
    
    :root {
    	--yellow: #FAE100;
    }
    ```
    

### Icons

- 아이콘을 추가하는 방법은 2가지가 있다.
    
    (1) svg 파일 이용
    
    - 픽셀이 없는 이미지 파일 형식. 수학(path element)으로만 구성된 형식
     좌표로 되어 있어 원하는 만큼 늘릴 수 있음
    - CSS를 통해 크기, 스타일 조절
    
    (2) 아이콘 사이트에서 <i> element를 이용해서 사용
    
    <aside>
    👊 **아이콘 사이트**
    
    Heroicons = 귀엽고 무료 아이콘. 필요한 아이콘 없을 수도.
    
    FontAwesome = Most popular. 유료와 무료 모두 있음
    
    - 사용방법
        - 이메일 입력해서 회원 가입. code kit 사용
        kit code는 src를 보면 자바스크립트 파일인 경우가 많음
        해당 링크를 보면 많은 클래스명과 폰트를 import하고 있음
        프로버전 구입할 것 아니라면 굳이 가입할 필요 없음
            
            > <script src=”https://kit.fontawesome.com/6478f529f2.js” crossorigin=”anonymous”></script>
            > 
        - **<script>는 언제나 body element 닫기 직전에 있어야 함**
        - 원하는 무료 아이콘의 i element 복사 붙여넣기.
        i element 내부에 있는 class는 js에 관한 것이므로 건드리면 안됨.
    </aside>
    
- i는 icon을 의미한다.
- 아이콘 사이즈 조절 방법
    1. fontAwesome에는 각 아이콘별로 사이즈 크기에 관련된 옵션 class가 있다.
    원하는 아이콘에서 크기 설정을 확인한 후 class에 추가해주면 된다.
    2. 아이콘의 크기는 font-size와 관련있기에 그 부분을 관리해도 된다.

### status-bar CSS

- class를 이용해서 접근
하위 요소는 pseudo selector / combinator를 적절하게 이용함
아이콘의 기본 설정과 같이 해당 요소를 특정지을 class가 이미 존재한다면 그것을 이용해도 좋음
- `font-family` 속성 : 폰트 설정.
여러가지 폰트 입력되는데 앞의 폰트가 실행되지 않을 경우 다음 폰트 실행
    - google-font를 이용하면 원하는 폰트를 선택할 수 있음 =
    select this style 선택 → embed (by `html내 link` or `CSS에 import` )
    ⇒ 둘 중 import 하는 방법을 좀 더 추천함 / CSS 최상단에 import 입력
    선택할 수 있는 옵션이 많은 것들이 있음
    (불필요한 폰트는 선택 X해야햠, 파일 추가의 개념이기에 웹 사이트 무거워짐)
- space-between을 할 경우 좌우 요소의 크기(width)가 다르면 가운데 있는 요소가 전체의 가운데에 위치하지 않음.

### **justify-content 대신 컨테이너 하나를 중심에 놓는 CSS hack**

(좀 이상할 수 있어도 어디에서나 작동함. 그래서 hack이라고 하는 것.)

1. 부모 element에 display: flexr; justify-content: center; 입력
    
    ```css
    .status-bar {
    	display: flex;
    	justify-content: center;
    }
    ```
    
2. 부모 내 모든 자식 element에 33%의 width 설정
    
    ```css
    .status-bar__column {
    	width: 33%
    }
    ```
    
3. 자식 중 2번째 요소에 (inline 이어도) flex + 가운데 정렬
    
    ```css
    .status-bar__column:nth-child(2) {
    	display: flex;
    	justify-content: center;
    }
    ```
    
4. 자식 중 마지막 요소에 flex + 오른쪽 정렬
내부에 있는 아이콘의 수직 정렬이 안맞기에 align-items: center 추가
(inline은 height가 글씨의 크기이기에 따로 높이 설정 안해도 됨)
    
    ```css
    .status-bar__column:last-child {
    	display: flex;
    	justify-content: flex-end;
    	align-items: center;
    }
    ```
    

### welcome-header CSS

- reset CSS를 적용했기에 top-bottom 식으로 margin부터 주는 과정을 진행
- display:flex 이후 justify-content: center를 줘도 되겠지만,
텍스트 가운데 정렬에 관해서는 `**text-align:center;**`를 줄 수 있음
- 클론코딩에 사용하기 유용한 extenstion 추천
    
    > **page ruler redux** : 클론할 페이지, 이미지의 margin이 어느정도인지 확인 가능
    **colorzilla** : 페이지, 이미지의 색상값 스포이드
    > 
- 글씨 색을 변경하는 방법
    1. **`color: gray;`**
    2. **`opacity: 0.7;`**
- google font에서 받은 글씨의 굵기 설정
    
    google-font에서 가져온 font의 경우 option에서 선택한 값 (ex. 600) 등을
    `font-weight: 600;`을 입력
    

### login-form input CSS

- id라고 설정해놨다면 # 쓰는 것 잊지말기.
- input 요소들이 가로로 붙어있지 않고 세로로 정렬되길 원함
    
    = form id 선택자에 display: flex; flex-direction: column설정
    (각 input에 block 설정해도 되긴함)
    
- input과 body의 사이의 좌우 여백을 만들고 싶음
= margin (content border의 바깥 부분) : 0px 30px; 설정
- input 디자인 바꾸기 (접근은 `**#login-fom input**`으로)
    1. content 내부의 여백 (padding) 값 주기 ⇒ **`padding: 15px 0px;`**
    2. 테두리 바닥 제외 없애주기 (rgba의 a는 opacity)
    ⇒ **`border: none;` `border-bottom: 1px solid rgba(0,0,0,0.3)`**
    3. placeholder 내 글씨색 변화
    ⇒ login-form id에만 해당하는 input의 placeholder값 변경
        
        ```css
        #login-form input::placeholder {
        	color: rgba(0, 0, 0, 0.4)
        }
        ```
        
    4. input에 사용자가 값을 입력할 경우 ouline이 없게끔
        
        ⇒ 현재 input 이외 모든 input에 적용하고 싶으므로, reset.css에서 설정
        
        ```css
        @reset.css
        
        input:focsu {
        	outline: none;
        }
        ```
        
    5. login-form 내 input에서 값 입력 시 border-bottom의 색상 변화
        
        ⇒ **`#login-form input:focus {border-color: var(--yellow);}`**
           (variable.css import 필수)
        
    6. input:focus 상태 이전과 이후 사이 부드러운 연결 주기
    ⇒ **`login-form input {}`**에 **`transition: border-color .3s ease-in-out;`** 설정

### login-form button CSS

- button을 input type=”button”으로 할 경우 input CSS가 동일하게 설정된다.
⇒ css의 **`:not()`** 속성으로 input submit 이외의 input type에 설정 필요
    input submit 속성에는 attribute selector를 활용해 CSS 설정
    
    <aside>
    👊 CSS의 **`:not()`** 속성
    
    뭔가가 적용되는 것을 원하지 않을 때
    (p 태그가 아닌 경우, .fancy 등의 class 명을 갖지 않을때 등)
    
    ⇒ 괄호 내 조건에는 적용되지 않길 원하는 요소와 적용된 요소와 구분될만한 선택자 입력 (해당 조건을 제외하는 나머지에 적용하고 싶다는 말과 같음)
    
    </aside>
    
    ```css
    #login-form input:not([type="submit"]) {
    	border-botttom: 1px solid rgba(0,0,0,0.2);
    	transition: border-color 0.3s ease-in-out;
    }
    #login-form input[type="submit"] {
    	background-color: var(--yellow);
    	cursor: pointer;
    }
    ```
    
    - attribute selector (특성 선택자) : 속성 일치 여부가 선택할 요소가 됨
    - 해당 코드는 “type이 submit이 아닌 login-form 내 input(input type=”text”와 “password”)에게 border-bottom 속성과 focus 시 transition 속성을 부여한다”는 의미
    - CSS의 cascading 특징을 무시하지 말것. transition이 들어간 해당 CSS 코드가 #login-form input:focus 보다 위에 위치해야 올바른 변화값이 나타남

### login-form a CSS

- 글씨 가운데로 가게끔  ⇒ **`text-align: center;`**
- a의 default값 (밑줄, 파란색) 없애기 ⇒ **`text-decoration: none;`** + **`color:inherit;`**
    
    > 속성값 **`inherit`** = 부모 element로부터 색상 상속받는 것 (inheritance)
    여기서 부모 element는 form element. a 제외 나머지의 default color는 black
    > 
- 글씨 크기 설정 ⇒ **`font-size: 13px;`**

### login-from의 선택자 스타일 방식에 대해서

- 선택자 스타일은 개인의 취향에 따라 다른 것. 본인이 쓰기에 편한 방식을 채택하면 됨
    - header의 경우 BEM 방식 채택
    - ogin-form의 경우 가장 큰 영역만 class명을 지정한 후
    combinator와 pseudo selector를 사용해서 접근
        
        ⇒ 장점  : 여러 선택자를 연습해볼 수 있음
        

### CSS file organize

- 폴더 트리구조
    
    **`css`** folder
    
    **`component`** folder
    
    `status-bar.css`와 같은 모든 페이지에서 동일하게 보이는 것에 대한 CSS 설정
    
    **`screens`** folder
    
    login.css와 같은 각 페이지별 CSS 설정
    
    묶이지 않음 ⇒ `reset.css` / `styles.css` / `variable.css`
    
- styles.css에 import 하기
    
    = 구글 폰트 등 > css folder 내 파일 > compoenets 내 파일 > screens 순서 권장
    
    ```css
    @import "reset.css"
    @import "variables.css"
    
    /* Components */
    @import "components/status-bar.css"
    
    /* Screens */
    #import "screens/login.css"
    ```
    
    - 먼저 styles.css에서 작업한 후 파일 생성할 것을 권장
- styles.css에는 뭐가 있어야 하나?
    
    = font-family와 같이 모든 스크린에 적용될 수 있는 스타일을 써놓는게 니꼬’s 스타일