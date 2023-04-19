# 코코아톡 6-2. Cloning Time

강의처: 노마드코더

기록 날짜: 2023/04/16 → 2023/04/18

세줄 요약: animation 효과 및 media query 적용시키기 (box-sizing, z-index, order porperty, will change, visability)

주제: CSS, HTML

- 목차

### VSC 단축키 모음

- element 내부의 element 구조와 개수, class, content까지 입력 가능
    
    `>` 이용해서 내부 부모-자식 관계 표현 / `* num` 이용해서 해당 element 개수 표현
    `element.class-name` 입력해서 class 명 설정 (element 설정 안할 경우 div로 표현)
    `{}` 이용해서 content 표현
    
    ex. `**ul > li * 4 > a**`
    
- `**ctrl + D**` = 코드 내 동일한 내용 선택 가능

## Friends 페이지 만들기

- index.html에서 중복된 요소는 그대로 가져옴

- 최종적으로 만들 페이지와 비교했을 때 스타일이 겹친다면
component css folder로 넣을 생각을 하자
(ex. 사용자 프로필 화면 === user-component : photo와 text 구성)

### Navigation bar - HTML

- nav element 안에서 작업
- navigation은 ul > li > a > i 의 구조를 가짐
(검색엔진 구글도 navigation을 찾아서 ul > li 안에 있는 link를 가져오게끔 설정)

### header & friends-display link - HTML

- header 트리구조
    
    header.screen-header
    
    h1.screen-header__title
    
    div.screen-header__icons
    
    span*3>i
    

### Navigation bar - CSS

- nav의 class명이 nav여도 상관 없음 (CSS에서 class 선택자를 통일시키기 위함)
- nav-bar.css 파일을 component에 넣고 해당하는 CSS를 입력했다면 import 단계 필수
- fontAwesome 내 documentation에는 size 관련 설정 등에 대한 정보가 문서화되어있음
- a element의 기본 글씨색을 부모 element의 것으로 없애는 것은 기본 설정값과 같기에
reset.css에서 a element에 대한 설정으로 저장해놓는 것이 좋음
a element의 색상을 변경하고 싶다면 부모 element에 색상을 입력시켜줘야함
    
    ```css
    @reset.css
    a {
    	color: inherit;
    	text-decoration: none;
    }
    ```
    
- **`position: fixed; bottom:0;`**로 화면의 하단에 맞춰주기
(status-bar도 fixed로 같이 맞춰주기)
- nav-link 내부에 채팅 개수를 표현하는 버튼이 존재함
    
    link에 `**position: relative;**`를 채팅개수 span에 `**position: absolute;**`를 줌
    (span의 경우 너비와 높이가 없기에 display: block 이나 flex 설정을 준다.
    
- nav-link 중 더보기 link에도 공지사항등의 변경이 있을 경우 빨간 점이 있음
이것 역시 position: relative와 absolute를 설정해줘야함

<aside>
👊 **CSS는 cascading 언어이기에 입력 순서가 매우 중요하다.**

font → reset.css → variables.css → components → screens

만약 variables.css를 components나 screens 아래에 위치시킨다면 적용 안됨 주의

</aside>

<aside>
👊 **box-sizing: border-box;**

- CSS는 기본적으로 width와 padding을 모두 설정할 경우 기본적으로 각각의 값을 유지하기 위해 padding값 만큼 box를 키운다
- **`box-sizing: border-box`**라고 할 경우 padding에 상관없이 box의 사이즈를 width값으로 유지하라고 설정한 것과 같이 된다.
padding의 사이즈만큼 content의 사이즈는 줄어든다.
</aside>

### user-component - HTML

- 공통적으로 작동하는 부분에 대해서 component 작업을 한다고 생각하자.
- 트리구조
    
    `**div.user-component**`
    
    **`div.user-component__column`** (필수 요소들, photo, titile, subtitile 들어가는 자리)
    ⇒ 기본 사이즈 이외 다른 사이즈가 나올 경우 **`user-componenet__column—xl`**과 같이 추가적인 클래스명을 덧붙이고, 바뀌는 요소만 변경해준다.
    
    **`img.user-component__avatar`**
    ⇒ 기본과 사이즈 다를 경우 class명 추가
    
    **`div.user-component__text`**
    
    **`h4.user-component__text__titile`**
    
    **`h6.user-component__text__subtitile`**
    ⇒ subtitile은 존재하지 않을 때는 주석처리
    
    **`div.user-component__column`** (부가 요소들 들어가는 자리)
    

### friends__screen__channel - HTML

- BEM 방식의 class name이 길어지지만, BEM을 쓸 때 해줘야 함
- 나는 아코디언 효과 줄거임
- 트리구조
    
    friends__screen__channel
    
    user-component user-component--sm
    
    위에서 사용한 user-component 복붙 후 두번째 자식 요소 (column) 수정
    

### user-component - CSS

- component와 component__column:first-child에 flex / align-items:center 설정
(,로 두 클래스 모두에게 스타일 적용할 것)
- user-component__avatar의 경우 페이지마다 큰 / 중간 / 작은 이미지가 있음
    
    중간 사이즈를 기본으로 만들어주고, 다른 크기는 class를 추가해준다.
    ex. —header
    
- 부모 element의 좌우의 padding (또는 자식 element의 margin)은 다른 component에서도 동일하게 적용되는 요소이기에 **`variable.css`**에 변수로 적용한다.
ex. **`--horizontal-space: 25px;`** 이후 값이 들어가는 위치에 변수를 대신 넣어주면 된다.

## 나머지 페이지 만들기

- 하나를 복붙해서 쓰는 경우가 많기 때문에 비워진 내용은 (a element의 href) 미리 채워놓자.
- margin 값으로는 negative value도 있으니, 잘 활용하자
- 공통적으로 보이는 요소가 있다면 다른 요소들과 공통적으로 적용되는 것들을 묶어서 component 파일에 옮기고, class명을 추가해준다.
(import 하는 것 잊지말기)
    - 처음부터 완벽하게 component를 나눠서 만들 필요 없다. 만들다가 중복인 것 같으면 이전에 작업한 내용을 component로 만들고 html과 css에서 component를 변경해주면 된다.
    - 이때 각 페이지마다 component에서 요소가 조금씩 달라진다면,
    class명을 추가하고 class명을 선택한 css를 해당 screens 내 css 파일을 만들어서 작업한다.

- 공통적으로 사용되는 속성이 있다면 역시 variables.css에 넣고 변수화해서 같은 속성을 가질 수 있도록 하는 것이 좋다.
    
    (border에 있는 구분선 등)
    
- 대문자는 디자인적 요소이기에 대문자로 보여지길 원하더라도 HTML 상에서는 소문자로 작성, 이후 CSS에서 대문자로 변환할 것.
    
    ⇒ 변경하는 방법 = **`text-transfomr: uppercase;`**
         
    
- |와 같은 divider 만드는 방법 ⇒  **`width:1px; height:15px;`**
- modifier는 중요하다.
    
    기존의 것으로 모두 가져오면서 CSS를 덮어씌워서 필요한 부분만 바꾼다.
    
    modifier의 원본이 되는 class를 먼저 입력한 후 modifier class를 같이 입력한다.
    
    최상단에 위치한 것만 modifier를 적용하고 이후 CSS를 combinator를 이용
    

### Z-index

- layer의 순서가 몇번째인지 나타내는 것.
- display 작업을 하거나, position이 고정(fixed), 절대위치(absolute)의 경우 layer를 갖게 됨
- z-index의 기본값은 0이며, 화면 상에서 layer가 위에 위치할수록 z-index의 값은 크다.

### 테두리 각 꼭지점에 radius를 주는 방법

- **`border-top(bottom)-right(left)-radius`** 를 준다.
    - 왼쪽 위 `**top-left**` / 왼쪽 아래 `**bottom-left**`
    - 오른쪽 위 `**top-right**` / 오른쪽 아래 `**bottom-right**`

### order property

= **flex children에서만 적용** 가능한 속성

- 순서를 바꾸는 방법 중 하나
- 0부터 시작하며 0에 위치하는 것이 flex의 가장 첫번재에 오게 된다.

## animation 효과 주기

- 좀 더 상호작용하는 효과를 줄 수 있음

### splash Screen (animation)

- 원하는 페이지에 들어오기 전 보이는 로딩 화면처럼 보이게 할 예정
    - 만드는 방법 (HTML과 CSS 기본 작업)
        1. 원하는 페이지 가장 마지막 부분에 div.splash-screen 추가
        2. splah screen에 들어가고 싶은 내용을 html에 넣고 CSS 작업 시작
        3. position: absolute 설정 후 body를 relative로 잡아 보여지도록 하기
        width와 height를 100vw(vh)로 맞춘 후 top: 0;를 준다.
- 여러 요소에 대해서 시간차를 두고 animation 효과를 주고 싶다면, **`animation-delay`**를 사용하면 된다.
    
    하지만 이후의 animation이 진행되는 요소는 animation이 동작하기 전까지 해당 위치에 존재할 수 있기에 초기값에 transform과 opacity를 준다면 애니메이션 유무에 상관없이 바닥에서 시작한다.
    
    - 페이지에 splash screen이 있다면 해당 페이지의 애니메이션은 볼 수 없다

<aside>
❗ will-change property

브라우저에게 어떤 것이 변화할 것이라는 것을 명시해주는 역할

브라우저는 애니메이션을 보다 나은 형태로 부드럽게 만들어줌

(브라우저 돕는 역할. 브라우저가 그래픽카드를 이용해 애니메이션 가속화하게 함)

</aside>

<aside>
❗ focus-within

내부에 focus된 element가 있는지 확인하는 것

</aside>

- 만드는 방법 (animation)
    1. @keyframes animation_name {} 안에 상황 부여
        
        keyframe 내부에 작성하는 transform은 공백을 기준으로 다른 효과를 줄 수 있음
        
        <aside>
        ❗ animation의 네번째 속성값들
        
        - forwards
            - animation의 마지막 값을 애니메이션 끝나고도 유지하고 싶을 때
            - class 선택자 내부에 마지막 값을 저장하는 방법과 동일한 효과
        - infinite
            - 해당 애니메이션이 페이지 내에서 무한 반복하고 싶을 때
        </aside>
        
    2. 문제 = animation이 끝난 이후 상태가 유지되기 때문에 해당 layer가 최상단에 위치해 아래 페이지의 요소를 선택할 수 없음
        
        display: none; 속성을 부여해도 선택 불가
        
        <aside>
        ❗ visability: hidden;
        
        - 마우스에 걸리지않게 빠져버리게 하는 속성
        - 브라우저가 이 element를 무시하도록 하는 기술 같은 것. 실제로는 해당 요소가 가장 위에 있음
        - 뭔가를 숨기거나 html상에서 해당 요소를 제거하고 싶다면 이 속성을 부여하면 안된다.
            
            Javascript를 사용해야 함
            
        </aside>
        

## Media-query

- 원하는 페이지 html 가장 마지막에 div.no-mobile을 만든다.
- no-mobile.css를 css/component에 추가
    - position: absolute;로 body에서의 위치 수정이 가능하도록 한다.
    - z-index: 99;로 다른 layer보다 가장 최상단에 위치하도록 한다.
- @media screen and (max-width:) {} ⇒ 범위가 최대 645px를 안넘기면 안보이지만, 넘기면 해당 화면이 z-index 최상단으로 보임
- landscape나 portrait에 대한 설정을 추가할 수도 있음