# JS - History / JS & DOM

강의 날짜: 2023/03/13

강의처: KDT

기록 날짜: 2023/04/07 → 2023/04/08

세줄 요약: ECMAScript (JS의 표준화) / JS 실행 환경 종류 / DOM 정의&선택&조작

작성 완료: Yes

주제: JS

강의필기: [0314 KDT 강의 필기](/03_language/04_Javascript/0314_KDT_JS_DAY2.pdf)

- 목차

# JS - History of Javascript

### 이번 수업의 목차

1. 웹 브라우저와 Javascript
2. Javascript의 표준화

### 학습 목표

- Javascript의 탄생과 초기 개발 과정을 이해할 수 있다.
- 현재 웹 개발에서 Javascript가 가지는 역할과 중요성을 인식할 수 있다.

---

## 웹 브라우저와 Javascript (History)

### 1994. 웹 브라우저의 상용화

- 1994년, Netscape사의 최초 상용 웹 브라우저 Netscape Navigator 출시
    
    ⇒ 당시 약 90% 이상 시장 점유율 추정
    

### 1995. 웹 브라우저 경쟁

- 1995년, Microsoft 사의 Internet Explorer(IE) 출시
- Netscape는 IE와 경쟁할 차기 웹 브라우저 개발 착수
동적 기능 제공을 위한 새로운 언어 개발 Project 진행

### 1995. Javascript의 탄생

- Netscape 소속 개발자 Brandon Eich가 Mocha 언어 개발
- 이후 LiveScript로 이름 변경했으나, 당시 인기 프로그래밍 언어인 JAVA 명성에 기대보고자 Javascript로 이름 변경
- Javascript는 Netscape Navigator 2.0에 탑재… 큰 인기

### Javascript의 파편화

- Microsoft 사
Javascript 파생 버전인 Jscript IE 3.0에 채택
- 많은 회사들이 자체 Javascript 탑재
→ 독자적 업데이트
- 같은 코드가 브라우저마다 다르게 동작하는 등의 문제 발생
    
    **“Cross Browsing Issue”**
    

⇒ JS 표준화의 계기가 됨

### ~2002. 1차 브라우저 전쟁

- MS사 IE를 자사 윈도우 운영체제에 내장… 무료 배포
MS사의 공격적 마케팅, 자금력, 윈도우 운영체제 점유율로 Netscape 몰락
- 2002년 IE의 시장 점유율 96% 달하며 MS사 승리
Brandon Eich 등의 Netscape 핵심 개발진 모질라 재단 설립
2003년 Firefox 브라우저 (오픈소스 브라우저) 출시

### 2008. 2차 브라우저 전쟁

- 2008년 구글 Chrome 브라우저 출시
(크로미움 기반 브라우저 엔진 내장)
출시 3년만 Firefox 점유율 넘어섬,
이후 반년만 IE 점유율 추월
- Chrome 장점
= 빠른 속도, 압도적 성능, **엄격한 웹 표준 준수**, **강력한 개발자 도구 제공**

⇒ 웹 표준의 발전과 웹 애플리케이션의 대중화에 큰 기여

### Javascript 현황

- 현재 Chrome, Firefox, Safari, MS Edge 등 다양한 웹 브라우저 출시
⇒ 웹 브라우저 시장 다양화
- 브라우저 내 웹 페이지 동적 기능 구현
→ Node.js와 같은 서버 사이드 / React, Vue 등의 다양한 프레임워크와 라이브러리 개발
⇒ 웹 개발 분야 필수 언어로 자리잡음
    - 웹페이지 동적 기능
    = 사용자 입력 따른 페이지 내용 변화
    = 애니메이션 효과 적용 등

---

## Javascript의 표준화

1차 브라우저 전쟁 시절 JS의 파편화가 발생하면서 표준화의 필요성이 대두됨

### ECMA Script

- Ecma Internation (정보와 통신 시스템을 위한 국제적 표준화 기구)이 정의하고 있는 표준화된 스크립트 프로그래밍 언어
- JS의 파편화를 막기 위해 1997년 ECMA에서 ECMAScript라는 표준 언어를 정의 → 독자적 발전하며 Javascript보다 더 많은 기능 제공하게 됨
    
    <aside>
    ❗ **JS의 언어발전 속도가 느렸던 이유**
    
    1. JS의 파편화
    2. IE의 장기 집권 (당시 MS사는 ECMAScript를 따르지 않고 본인들만의 방식으로 진행 중이었음)
    </aside>
    
- 2009년 ECMScript 5 (ES5)에서 안정성과 생산성 크게 높임
- 2015년 ECMAScript 2015(ES6)에서 객체지향 프로그래밍 언어로써 많은 발전을 이룸 ⇒ 역사상 가장 중요한 버전으로 평가됨
    - 객체, 변수 선언 (let, const), Template Literal (템플릿 리터럴) 등이 이때 이후 개발
- Javascript는 ECMAScript의 구현 언어 중 하나

---

---

# Web - Javascript and DOM

### 목차

1. Javascript 개요
2. DOM 기본 개념
3. DOM Query (선택)
4. DOM Manipulation (조작)

---

### 학습 목표

- 웹 브라우저에서의 Javascript의 역할을 정의할 수 잇다.
- 웹 페이지의 HTML과 CSS를 Javascript에서 다룰 수 있는 DOM에 대해 이해하고
웹 페이지의 요소들을 조작할 수 있다.
- DOM 조작에 사용되는 메소드의 속성을 적절히 사용할 수 있다.

## Javascript 실행 환경

<aside>
❗ **JS는 웹에서 어떻게 작동할까?**

- Javascript는 웹 브라우저 상에서 **웹 페이지의 동적인 기능**을 구현하기 위해 사용된다.
- Javascript는 웹 브라우저에 내장된 Javascript 엔진에 의해 브라우저에서 실행된다.
    - Javascript 엔진은 브라우저마다 JS 실행 엔진이 존재하며, Chrome의 경우 V8엔진을 이용한다.
</aside>

### HTML Script 태그

- HTML 문서 내부에 <script> element를 이용해 JS를 실행
- <script>는 주로 <body> 내부 최하단에 위치한 경우가 많다.
[script-태그는-어디에-위치해야-할까요 => velog](https://velog.io/@takeknowledge/script-%ED%83%9C%EA%B7%B8%EB%8A%94-%EC%96%B4%EB%94%94%EC%97%90-%EC%9C%84%EC%B9%98%ED%95%B4%EC%95%BC-%ED%95%A0%EA%B9%8C%EC%9A%94)

```html
<body>
	<script>
	</script>
</body>
```

### JS 확장자 파일

- 프로젝트 폴더 내 JS 확장자 파일을 생성해 HTML 문서와 연결
    - HTML 문서<script> element에 src attr로 연결한다.

```html
<body>
	<script src="hello.js"></script>
</body>
```

### 브라우저의 Console

- 브라우저 개발자 도구 내에 있는 Console에서 Javascript를 직접 입력
- 브라우저 내에서 바로 실행하고 결과를 확인할 수 있다는 장점이 있음

---

## DOM의 기본 개념 (JS가 Webpage 요소를 동적으로 만드는 방식)

### DOM API

- Document Object Model. 문서 객체 모델
    
    ⇒ 문서를 객체로 바라봐 다른 Programming 언어들이 접근할 수 있도록 함
    
- 브라우저가 제공하는 API로 태그나 내부 콘텐츠 등을 보여준다.
- **웹 페이지(Document)를 구조화된 객체로 제공하며, 프로그래밍 언어가 웹 페이지를 사용할 수 있게 연결시킴**
- 문서 (Document, HTML CSS JS 문서 등)는 웹 브라우저를 통해 해석(시각화)되어 화면에 나타난다.
DOM은 이러한 문서를 조작하는 방법을 제공하는 API
- 특히 브라우저는 HTML 문서를 해석해 DOM tree라는 객체의 트리로 구조화한다.
- DOM에서 모든 요소, 속성, 텍스트는 하나의 객체이다.
- 가장 최상위 객체는 window > document이고 나머지는 document 객체의 자식의 구조로 된다.
실제 우리가 조작할 때 접근하는 위치는 document

<aside>
❗ “브라우저 ⇒ DOM tree라는 객체의 트리로 문서(HTML) 구조화”
”프로그래밍 언어 (JS)는 각 객체를 선택(탐색, 접근), 조작해 웹 페이지를 동적으로 만든다”

</aside>

> **<정리>**
**웹페이지를 동적으로 만드는 것 == 웹 페이지를 조작하는 것**
> 
> 
> **조작 == 생성(C), 수정(U), 삭제(D)**
> 
> **조작하기 위한 순서**
> 
> 1. **조작하고자 하는 요소를 선택 또는 탐색**
> 2. **선택된 요소의 콘텐츠 또는 속성을 조작**

<DOM tree>

![https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/DOM-model.svg/1200px-DOM-model.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/DOM-model.svg/1200px-DOM-model.svg.png)

- Parsing (파싱)
    - 구문 분석, 해석
    - 브라우저가 문자열을 해석해 (element, class, attr, textContent 등을) DOM Tree로 만드는 과정

### ‘document’ object

- 웹 페이지 객체
- DOM Tree의 진입점 (가장 최상단)
- 페이지를 구성하는 모든 객체 요소를 포함한다.
- 만약 우리가 웹 페이지 탭의 제목에 접근하고 싶다면
`document.title` 을 입력하면 된다.

---

## DOM Query (선택)

객체를 조작하기 위해 선행되어야 하는 일 == 객체 선택하기 ==DOM Query

객체 선택은 JS를 이용해서 하기에 문법 사항 역시 JS 문법과 변수명 작성 규칙을 따른다.

DOM Query의 선택자는 CSS 선택자( `태그 접근` `class 접근` `id 접근`)를 이용한다.
메서드의 형태로 접근하기에 함수 내 인자의 위치에 선택자를 입력하면 되며 문자열 데이터로 입력한다.

### 요소 하나 선택 (querySelector)

> document.querySelector(’selector’)
== document 객체 내 querySelector라는 함수(메서드)를 이용해 인자에 해당하는 선택자에 접근한다.
> 
- 제공한 선택자와 일치하는 element 한개를 선택
- 만약 해당하는 인자가 여러개라면 제공한 CSS selector를 만족하는 첫번째 element 객체를 반환한다.
- 만약 해당하는 인자가 없다면 null을 반환한다.

### 요소 여러개 선택 (querySelectorAll)

> document.querySelectorAll(’selector’)
== document 객체 내 queyrySelectorAll이라는 함수(메서드)를 이용해 인자에 해당하는 모든 선택자에 접근한다.
> 
- 제공한 선택자와 일치하는 여러 element를 선택
- querySelectorAll을 통해 선택된 DOM API는 NodeList라는 Array의 형태로 반환된다.
Array의 형태로 들어오기 때문에 index를 활용해 반복문으로 활용 가능하다.

---

## DOM Manipulation (조작)

### DOM 조작 CASE들

- 조작 전에는 querySelector( ) 나 querySelectorAll( ) 메서드를 활용해 변수 선언을 하는 **선택과정**을 먼저 해야한다.
1. 속성 (attribute) 조작 = element의 attr의 값 조작
    1. 클래스 속성 조작 = element의 attr 중 class attr과 관련해서 값 조작
    2. 일반 속성 조작 = element의 class 이외의 attr 관련 값 조작 (class도 attr이기에 해당 방법을 이용할 수 있긴 함)
2. HTML 콘텐츠 조작 = element 중 content가 있는 element 내부 콘텐츠 조작
3. DOM 조작
4. style 조작

<aside>
❗ HTML tag (element)의 구성요소

> <tag class=’’ href=’’ style=’’> content </tag>
> 

DOM을 통해 tag에서 접근 & 동적으로 바꿀 수 있는 것들

- tag (DOM element) 자체 (`생성` / DOM tree 내부에 부모-자식 관계 `추가`/`삭제`)
    
    - document.createElement(’tagName’) = 문서 내 element 추가/아직 관계 설정 X
    - element1.appendChild(element2) = 부모-자식 관계 추가
    - element1.removeChild(element2) = 부모-자식 관계 삭제
    
- class (`조회` / `생성&조작` / `삭제`)
    1. element.classList 속성 접근 ⇒ DOMTokenList의 유사배열 형태로 반환
        
        - element.classList.add(’className’) = element class attr에 class 추가
        - element.classList.remove(’className’) = element class attr에 class 삭제
        
- attr (`조회` / `설정&수정` / `삭제`)
    
    - element.getAttribute(’attrName’) = element 내 attrName 해당 속성값 조회
    - element.setAttribute(’attrName’, ‘attrValue’) = element내 attrName 해당 속성값 설정
      (없을 경우 새로 attrName 추가 후 값 추가)
    - element.removeAttribute(’attrName’) = element 내 attrName 관련 항목 삭제
      (삭제 후 조회 시 null 반환됨)
    
- style (`조회` / `수정`)
    1. `element.style` 속성 접근 ⇒ CSSStyleDeclaration object로 반환
        
        - `element.style.property` 에 할당 연산자 = 사용해 값 재할당 (수정)
        
- content (`조회` / `수정`)
    1. `element.textContent` 속성 접근 ⇒ content에 해당하는 내용 문자열로 반환
        
        - `element.textContent`에 할당 연산자 = 사용해 값 재할당 (수정)
        
</aside>

### DOM 요소 조작

= DOM의 element, 즉 HTML의 tag를 생성하고,
   element를 다른 기존의 element들과 부모-자식 관계를 추가/제거

- (생성 C) **`document.createElement()`** 메서드
= 문서 내에 tag를 생성한다. 아직 DOM tree 내부에서 관계를 맺진 않음
= 변수 선언을 통해 생성한 tag를 추가할 수 있도록 만든다.
= 인자로는 추가할 tag명을 문자열로 입력받는다.
    
    ```jsx
    const h1Tag = document.createElement('h1')
    h1Tag.textContent = '제목'
    ```
    

- (추가 C) **`element.appendChild()`** 메서드
= element에 부모-자식 관계를 부여한다.
= `document.createElement()` 메서드로 element를 만들었을 경우에는 반드시 이 과정을 거쳐야 한다.
= 이미 문서에 존재하는 요소를 다른 요소의 자식으로 삽입하는 경우에는 위치 이동의 개념으로 작동한다.
= element로는 부모관계에 해당하는 element를 사용한다.
   (사용 전 항상 querySelector로 요소 선택 과정을 거친다)
= 인자로는 자식관계에 해당하는 element를 입력받는다.
    
    ```jsx
    const h1Tag = document.createElement('h1')
    const divTag = document.querySelector('div')
    divTag.appendChild(h1Tag)
    ```
    

- (삭제 D) **`element.removeChild()`** 메서드
= element에 부여한 부모-자식 관계를 삭제한다.
= element로는 부모관계에 해당하는 element를,
   인자로는 자식관계에 해당하는 element를 입력받는다.
    
    ```jsx
    const h1Tag = document.querySelector('h1')
    const divTag = document.querySelector('div')
    divTag.removeChild(h1Tag)
    ```
    

### 속성 조작

= element의 attr의 값 조작

1. **클래스 속성 조작**
= element의 attr 중 class attr과 관련해서 값 추가 / 삭제
    - (R) **`element.classList`** 속성
    = element의 클래스 목록을 DOMTokenList (유사배열) 형태로 반환
        
        ```jsx
        const paraGraph = document.querySelector('.heading') //element 선택 후 변수에 저장
        console.log(paraGraph.classList) //element에 있는 class 속성값 DOMTokenList로 반환
        
        // DOMTokenList(2) ['title', 'heading', value:'title heading']
        ```
        
    - (C&U) **`element.classList.add()`** 메서드
    = element에 지정한 클래스 값 추가
    = 인자로는 추가하고자하는 클래스명을 문자열로 입력받는다.
        
        ```jsx
        const paraGraph = document.querySelector('.heading') //element 선택 후 변수에 저장
        console.log(paraGraph.classList.add('test') //선택 element 내 class 속성값에 test 추가
        
        // DOMTokenList(3) ['title', 'heading', 'test', value:'title heading test']
        ```
        
    - (D) **`element.classList.remove()`** 메서드
    = element에 지정한 클래스 값 제거
    = 인자로는 삭제하고자하는 클래스명을 문자열로 입력받는다.
        
        ```jsx
        const paraGraph = document.querySelector('.heading') //element 선택 후 변수에 저장
        console.log(paraGraph.classList.remove('test') //선택 element 내 class 속성값에서 test 삭제
        
        // DOMTokenList(2) ['title', 'heading', value:'title heading']
        ```
        

1. **일반 속성 조작**
= element의 class 이외의 attr 관련 값 추가 / 삭제
    (class도 attr이기에 해당 방법을 이용할 수 있긴 함)
    - (조회 R) **`element.getAttribute()`** 메서드
    = 해당 element에 지정된 속성값을 반환 
    =인자로는 조회하고자 하는 속성명을 문자열로 입력받는다.
        
        ```jsx
        const aTag = document.querySelector('a') //element 선택 후 변수에 저장
        console.log(aTag.getAttribute('href')) //element에 있는 'href' attr의 값에 접근한다.
        
        // http://www.google.com
        ```
        
    - (설정/수정 C&U) **`.setAttribute()`** 메서드
    = 지정된 element의 속성값 설정
    = 첫번째 인자로 바꿀 속성명을, 두번째 인자로 해당 속성의 바뀔 속성값을 입력받는다.
    = 속성이 이미 있으면 업데이트 / 없으면 지정된 이름과 값으로 새 속성 추가
        
        ```jsx
        const aTag = document.querySelector('a') //element 선택 후 변수에 저장
        aTag.setAttribute('href', 'http://www.naver.com') //element에 href 속성의 값을 naver 주소로 변경
        console.log(aTag.getAttribute('href')) //element에 있는 'href' attr의 값에 접근한다.
        
        // http://www.naver.com
        ```
        
    - (삭제 D) **`.removeAttribute()`** 메서드
    = element에서 지정된 이름을 가진 속성을 제거한다.
    = 인자로는 삭제할 속성명을 문자열로 입력받는다.
        
        ```jsx
        const aTag = document.querySelector('a') //element 선택 후 변수에 저장
        aTag.removeAttribute('href') //element에 href 속성의 값을 제거
        console.log(aTag.getAttribute('href')) //element에 있는 'href' attr의 값에 접근한다.
        
        // null
        ```
        

### HTML 콘텐츠 조작

= element 중 content가 있는 element 내부 콘텐츠 조작
= content는 브라우저 상에서 보이기 때문에 console.log 없어도 확인 가능

- (조회 R) **`element.textContent`** 속성
= element의 텍스트 콘텐츠를 표현
= 문자열의 형태로 콘텐츠값을 반환받는다.
    
    ```jsx
    const h1Tag = document.querySelector('.heading')
    console.log(h1Tag.textContent)
    
    // DOM 선택
    ```
    
- (수정 U) 조회하면서 선언한 변수의 값 재할당
    
    ```jsx
    const h1Tag = document.querySelector('.heading')
    h1Tag.textContent = '콘텐츠 수정'
    console.log(h1.Tag.textContent)
    
    // 콘텐츠 수정
    ```
    

 

### style 조작

= element의 모든 스타일 속성 목록을 포함하는 style property를 이용해
    해당 element에 있는 스타일에 접근, 수정한다.

- (조회 R) **`element.style`** 속성
= element의 모든 스타일 속성 목록을 포함하는 속성
   CSSStyleDeclaration {}의 object의 형태로 반환
   값이 있는 속성은 해당하는 값이 있지만 없을 경우 빈 문자열의 형태나 default 값으로 표현된다.
= style 속성에 먼저 접근한 후 세부적인 스타일 속성에 접근한다.
   이때, 세부적인 스타일 속성은 JS의 변수명 작성 스타일 (camelCase)를 따른다.
- (수정 U) 조회한 속성의 값 재할당
    
    ```jsx
    const pTag = document.querySelector('p')
    pTag.style.color = 'crimson'
    pTag.style.fonstSize = '3rem'
    ```
    

---

## 참고

### element 별 DOM property 확인하는 방법

- 개발자 도구 → Elements > element 선택 → Properties에서 해당 요소의 DOM property 확인 가능
    
    ![KakaoTalk_20230408_113947704_Edited.jpg](/03_language/04_Javascript/KDT_0313_JS_DOM_property.jpg)