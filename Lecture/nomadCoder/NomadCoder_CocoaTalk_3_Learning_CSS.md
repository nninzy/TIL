# 코코아톡 3. Learning CSS

강의처: 노마드코더

기록 날짜: 2023/04/05 → 2023/04/08

세줄 요약: CSS selector와 pseudo selector (state, combinator) / display:flex와 main-axis & cross-axis / position: static, fixed, relative, absolute

주제: CSS

### CSS를 HTML 페이지에 추가하는 방법

1. 각 tag에 style이라는 속성으로 각각 설정하는 방법
2. **HTML 파일 내부에 HTML과 CSS 파일을 한번에 해결하는 방법 : “inline CSS”라고 한다.**
    
    <head> 내부에 <style>를 추가해 그 안에 CSS 언어를 넣는다.
    
3. **HTML 파일 외부에 CSS 파일을 따로 만드는 방법 : “external CSS“라고 한다.**
    
    html과 같은 폴더에 위치한 CSS 파일은 style.css 라고 명명한다.
    
    <head> 내부에 <link/>를 통해서 연결한다.
    link 속성으로는 css 파일을 연결할 href, html과 css의 관계(stylesheet)를 표현할 rel이 필요하다.
    
    <link href=”style.css” rel=”stylesheet”/>
    
    장점 :
    
    - 분리된 파일을 사용하면, 다른 HTML 페이지에 style.css 파일을 사용할 수 있다.
    (다른 html 파일에도 동일한 효과를 적용할 수 있음)
    - HTML 파일 내에 위치한 것이 아니고, <link/> 한줄만을 이용한 것이기에
    html 자체 내 정보를 분산할 수 있어 코드의 가독성을 높일 수 있음

### Cascading Style Sheet의 의미

Cascading == **“위에서 아래로 순서대로 진행되는 것”**

Cascading code == **브라우저가 CSS 코드를 읽을 때 위에 있는 코드부터 차례로 읽는다.**

⇒ 동일한 선택자를 선택해 다른 속성을 줄 경우 **가장 마지막에 있는 코드가 적용된다.**

⇒ **코드의 순서가 결과에 영향을 미친다.**

---

## CSS 코드 구조

### 선택자 (Selector) :

HTML 요소를 선택하는 것 (HTML 요소를 가리키고 CSS로 잡아온다)

CSS는 HTML의 요소를 선택한 후 스타일을 부여하는 역할을 하기에, html의 요소를 선택하는 것이 중요하다.

선택자는 ,를 통해 여러개를 한꺼번에 설정할 수 있다.

<aside>
❗ CSS가 선택할 수 있는 것 : **전체 / tag명 / id값 / class값** 등

CSS에 사용되는 id값과 class값은 html에서 설정한 것과 동일한 이름을 가져야 한다.

- body 태그 내 모든 것을 선택하고 싶은 경우 :  ***을 이용한다.**
(inline 태그에도 적용된다. / cascading의 특성을 이용해서 가장 위에 사용하는게 좋다.
    
    ```css
    * {}
    ```
    
- tag명을 선택자로 이용할 경우 : 별다른 표현 없이 **tag명 그대로 사용**한다.
문제점 ⇒ html 내에 있는 동일한 tag가 모두 선택된다.
    
    ```css
    div {}
    ```
    
- id를 선택자로 이용하는 경우 : **id이름 앞에 #를 붙인다**.
    
    ```css
    #id-name {}
    ```
    
- class를 선택자로 이용하는 경우 : **class이름 앞에 .을 붙인다.
선택자로 class를 많이 사용한다.**
    
    ```css
    .class-name {}
    ```
    

[Pseudo Selectors](https://www.notion.so/Pseudo-Selectors-3cb464b9419249c79e53abd86f6667ea) ( 좀 더 세부적인 selector 방법)

</aside>

### 속성 (property) :

선택자에 부여할 스타일 속성들

선택자는 많은 속성을 가질 수 있다 ⇒ 선택자의 속성들을 하나로 묶기 위해 { } (중괄호, curly bracket) 사용

속성값은 많은 연습을 통해서 익숙해져야 함 (모두 다 외울 필요는 없음. 기본적인 동작 방식을 알 것)

<aside>
❗ 중괄호 안에 들어가는 속성의 형태 및 규칙

**속성명: 속성값;**

1. **속성명의 단어는 -(hyphen)을 통해 구분한다.** (공백, _(under_score), /(slash) 모두 사용 불가)
2. 속성명과 속성값은 : (콜론)을 이용해 구분한다.
3. CSS의 모든 속성에는 어떤 속성값이든 쓸 수 있으나 (에러 발생 X) 작동하지 않음
속성에 맞는 속성값을 입력해줘야 함
4. 속성값은 여러개가 올 수 있으며, 각각의 속성값은 공백을 통해 구분한다.
5. **속성값을 모두 입력한 뒤에는 반드시 ;(세미콜론)을 붙여서 속성값 지정이 끝났음을 알려줘야한다.
CSS에서 한 줄이 끝났음을 알려주는 요소이다.**

> CSS에서 사이즈를 나타내는 단위 예시
> 
> 
> px(pixels), em, point, percentage(%) 등
> 
</aside>

---

## 웹사이트를 구성하고 있는 box들 (display 속성)

### Blocks & Inlines

“웹사이트를 이루는 모든 요소들은 box이다. 우리는 box를 디자인해야한다.”

box는 block과 inline 두가지로 나뉘며 각각의 tag는 block 또는 inline 중 하나에 해당한다.

inline을 block으로, block을 inline으로 바꾸기 위해서는 선택자 속성 display를 바꿔주면 된다.
(display 속성값은 많은 것이 있지만 수업에서 다루는 것은 inline, block임)

### inline

- 웹 페이지 상에서 옆에 다른 요소가 올 수 있는 (같은 줄에 위치할 수 있는) 요소
- <span>, <code>, <img>, <a> 등 작은 글과 링크, 이미지가 여기에 해당한다.
(inline의 종류가 block보다 적기에 inline에 해당하는 것이 무엇인지 아는게 더 좋다)
- inline은 height와 width가 없으며, inline의 높이와 너비는 내부 글자 크기 & 길이와 같다.

### block

- 웹 페이지 상에서 옆에 다른 요소가 아무것도 올 수 없는 요소
- <div>, <header> 등이 여기에 속한다.
- block은 height와 width를 설정할 수 있으며
margin과 padding, border의 속성을 갖는다.

---

## margin, padding, border

- **block의 특징 세가지 : margin / padding / border (inline에도 적용가능)**
- 브라우저는 요소들에게 기본적으로 많은 style 속성을 준다. ⇒ 개발자도구에서 user agent stylesheet 내용
이 스타일 속성은 개발자가 원하는 값으로 덮어씌울 수 있다.
ex. 브라우저는 <body>에게 block 속성과 8px의 margin (공간 바깥의 여백)을 기본적으로 제공한다.

### **margin (block의 첫번째 속성)**

**box의 경계(border)의 / ‘바깥’에 있는 / 공간**

<aside>
💡 **Collapsing Margins**

margin top과 bottom에서(수직 상황에서)
두 block의 경계가 구분되지 않는다면, (두 block의 경계가 같다면)
하나의 margin으로 취급된다. (margin이 같아진다)

</aside>

### **padding (block의 두번째 속성)**

**box의 경계(border)의 / ‘안쪽’에 있는 / 공간**
box 내부에 다른 box가 있거나 content가 있다면 box의 경계로부터 여백을 만들어준다.

### **border (block의 세번째 속성)**

**box의 경계**

style로 두께, 색상, 테두리의 모양(border-style) 등을 설정할 수 있다.
border-style은 solid 이외에는 구려서 사용하지 않음

border 속성명을 이용해서 값을 설정할 경우 line-width / line-style / color의 순서대로 입력한다.

<aside>
💡 **margin / padding / border 값 설정의 shortcut**

1. 속성값이 **1개**일 때 : 네면 **모두 적용**
2. 속성값이 **2개**일 때 : 각각 순서대로 **수직, 수평**
3. 속성값이 **4개**일 때 : **시계 방향** 순서대로 / **위, 오른쪽, 아래, 왼쪽**

각각의 속성값은 공백을 통해 구분한다.

</aside>

<aside>
💡 브라우저 상에서 block들의 표현 규칙

**“위부터 아래로” + “왼쪽부터 오른쪽으로”**

따라서 하나의 box 안에 있는 box의 크기가 위에 있는 크기보다 크고, padding 값이 설정될 경우
위 & 왼쪽의 padding 값은 지켜지지만, 오른쪽과 하단에서 상위의 box를 튀어나온다.
여백 역시 동일하게 적용되는 것이 아니라 왼쪽과 상단 먼저 지켜지고 나머지는 여백으로 남는다.

</aside>

<aside>
💡 **inline에도 margin과 padding이 적용될까?**

**⇒ padding은 상하좌우 모두 적용 가능하지만,
margin의 경우 inline 요소는 높이와 너비가 없기에 좌우로만 가질 수 있다.**

**위 아래에 margin을 적용하고 싶으면 block 요소로 바꿔줘야한다.**

**inline에는 margin 과 같이 일부만 적용되는 속성도 있다.**

</aside>

---

## 기본 display 속성값에 변화주기 (inline-block과 flexbox)

### display = **“inline-block” ⇒ 잘 쓰지 않음, 더 좋은 방법이 있음**

inline과 block의 특징을 모두 갖는다
⇒ block의 특징인 width와 height를 갖고, 4면의 margin을 가짐
     inline의 특징인 옆에 다른 요소가 올 수 있음

**but, 너무 오래된 것이고, 문제가 많음**
ex. default 값으로 요소 사이에 빈 공간을 만들지 않았음에도 존재, 어디에도 표현되지 않음
ex.  정해진 형식이 없음.
       (요소 사이에 빈공간은 box의 크기가 늘어나면 빈공간이 변화함)
       (가장 오른쪽에 있는 박스의 오른쪽 여백이 가장 왼쪽 박스의 박스의 왼쪽 여백과 차이가 있다)
       (문제해결을 위해 사람이 일일이 체크해가며 여백을 주는 것은 너무 비효율적, 브라우저 크기 변화시 다시 맞춰야함)

### display = **“flex” ⇒ “inline-block을 대체할만한 것들”**

flexbox 내부에 속한 element 들은 bloc display 임에도 같은 줄에 다른 element를 둘 수 있음

장점 : 박스를 어떤 곳이든 둘 수 있음 / 굉장히 유연하며 2차원 레이아웃에서 아주 잘 작동함 / 사용 편의성

⇒ flexbox는 박스를 배열하는데 유용하다.

<aside>
❗ **flexbox를 사용하기 위한 규칙 3가지**

1. 자식 element에는 어떤 것도 적으면 안됨 / 부모 element에만 명시해야 함
    
    **== 자식 element를 움직이고 싶으면, 자식 element가 속한 부모 element를 flex container로 만들어야 함**
    
    “**부모 element가 자식 element를 제어함”**
    
    > 부모 element가 flex box일 경우 자식을 제어할 수 있는 것들
    (부모 element에 추가할 수 있는 속성)
    ⇒ display: flex; 일 때 사용할 수 있는 것들
    > 
    > 1. **justify-content** = “flex-start”(default) / “space-between” / “space-evenly” / “center” / “flex-end” 등
    >     
    >     **주축(default는 수평)을 기준**으로 **부모 element 내 자식 element의 위치(자식간의 여백 공간)를 결정**
    >     
    >     사이즈가 줄어든다면 자식 element가 본래의 크기를 유지하지 못하고 낑겨들어감
    >     
    > 2. **align-items** = “center” / “stretch”
    >     
    >     **교차축(default는 수직)을 기준**으로 **부모 element 내 자식 element의 위치(자식간의 여백 공간)를 결정**
    >     
    >     부모 element의 height(default 기준)
    >     
2. flex container는 **main-axis(주축)**과 **cross-axis(교차축)**을 가진다.
    
    default값 = 주축은 수평(horizontal) / 교차축은 수직(vertical)
    
    주축과 교차축의 수평, 수직은 변경할 수 있다.
    
3. 부모 element가 height를 갖고 있지 않다면
align-items: center;를 설정하더라도 바뀌지 않는다.
⇒ 이때는 viewport(vh)를 사용해서 노트북 화면 크기가 다르더라도 적용되게끔 하는 것이 좋다.
4. display:flex는 flex를 설정한 부모와 직계 자식간에서만 적용되는 것이다.
자식요소의 자식요소까지 flex를 설정하고 싶다면 자식 element에 다시 display:flex를 걸면 된다.
    
    ⇒ 원하는 만큼 flex 부모-자식 element를 만들어낼 수 있다.
    
</aside>

<aside>
❗ flex box의 속성들

<**flex의 주축과 교차축을 바꾸는 방법 ⇒ flex-direction>**

- flex-direction의 값
    1. row (default) : 수평
    2. column : 수직 ⇒ 주축(수평→수직)과 교차축(수직→수평) 기준을 바꿈
- reverse
    1. row-reverse: 오른쪽부터 시작
    2. column-reverse : 아래부터 시작

**<화면이 줄어들면 자식 element가 다음줄로 넘어가게 하는 방법 ⇒ flex-wrap>**

- flex-wrap의 값
    1. warp : 화면이 줄면 같은 줄에 있을 수 있는 최대 갯수만 같은 줄에 존재
    (element의 높이/너비는 초기 사이즈값 유지 가능)
    2. nowrap (default): 모든 요소를 같은 줄에 있게 만든다
    (element의 높이/너비는 초기 사이즈로 인식, 같은 줄에 있기 위해 변함)
- wrap-reverse : 가장 왼쪽에 있는 element부터 순차적으로 위로 올라감
(많이 사용하진 않지만 쓰일 일이 있을 수 있음)
</aside>

---

## Position 속성

- 레이아웃의 전체적인 변화보다는 위치를 아주 조금 상하좌우로 움직이고 싶을 떄 사용.

### position: fixed;

- 해당 element가 레이아웃 상에서 초기 위치에 계속 고정될 수 있도록 함
- 하지만, element에 top / left / bottom / right 속성값을 줄 경우 브라우저를 기준으로 위치가 변화한다. fixed된 element는 다른 layer에 있기에 다른 element가 해당 위치에 있더라도 신경쓰지 않는다.
- 해당 효과를 준 element는 다른 element보다 조금 더 사용자 쪽으로 나와있어 다른 element에게 영향을 주지 않음. (다른 layer에 있다고 표현함)

### position: static;

- position 속성의 default값
- 레이아웃이 element를 처음 위치하는 곳에 두는 것을 말한다.

### position: relative;

- element가 **처음 위치한 곳을 기준으로 상하좌우로** 위치를 바꾸고 싶을 때 사용
- position: relative를 줄 경우 top, bottom, left, right 속성을 사용할 수 있다.
- -10px 등의 값을 쓸 수 있다 (속한 위치 내에서 벗어날 수 있음)

### position: absolute;

- 가장 가까운 position: relative 부모를 기준으로 이동시켜준다.
(가장 최상위 relative 부모는 body element다)
⇒ 해당 element가 속한 위치에서 얽메이지 않고 더 상위의 부모와 관계를 맺을 수 있음
- position: absolute를 줄 경우 top, bottom, left, right 속성을 사용할 수 있다.
단, 반드시 relative 한 부모 element가 존재해야한다.

“굉장히 많이 쓰는 CSS 중 하나. absolute 설정 이후 relative 부모 설정 꼭 하자”

<aside>
❗ opacity 속성 = 투명도 속성

</aside>

---

## Pseudo Selectors

- 좀 더 세부적으로 element를 선택해주는 요소 (기존에 알고 있던 selector 보다 좀 더 자세한 방법

### element + ‘:’

element에 : 를 쓰면 사용할 수 있는 많은 옵션들이 나온다.

장점 = HTML 코드에 추가적인 class, id 지정을 하지 않고 CSS 선택만으로 스타일 변경 가능

- 자식 관계 선택
    
    ex. `div:last-child {}`
         전체 document 내에 있는 div 중 가장 마지막에 있는 것을 의미
    
    ex. `div:first-child {}`
         전체 document 내에 있는 div 중 가장 위에 있는 것을 의미
    
    ex. `span:nth-child(2),`
         `span:nth-child(4) {}`
          전체 document 내에 있는 span 중  2, 4번째에 있는 것을 의미
    
    ex. `span:nth-child(even) {}`
         전체 document 내에 있는 span 중 짝수번째에 있는 것을 의미
         even 대신 `2n`, odd 대신 `2n+1`도 사용 가능하다.
         ⇒ `3n + 1` (1, 4, 7… 2개씩 건너뛰기), `4n+1` (1,5,9… 3개씩 건너뛰기)도 가능
    

- attribute 속성을 갖고 있는 element 선택
    
    `input:required {}` = required 속성을 갖고 있는 input 선택
    (class 추가 없이 form에서 required 필드 보여줄 때 많이 사용)
    
    `input:optional {}` = optional 속성을 갖고 있는 input 선택
    

### **중요 state들 ⇒ `:` 을 이용한 것들**

해당 state 선택 후 button element의 default style을 바꿀 경우 border 등의 다른 style도 다시 style 설정을 해야함

1. **`element:active`** = 마우스 클릭을 눌렀을 때의 상태 (마우스 클릭을 뗄 경우 원 상태로 돌아감)
2. **`element:hover`** = 마우스 커서가 대상 위에 있을 때의 상태 (클릭 X)
3. **`element:focus`** = 마우스가 아닌 키보드로 선택됐을 때의 상태 (클릭 이후 tab 키 등을 이용해서 키보드로 상태를 옮길 때)
4. **`element:visited`** = only 링크에만 적용 / a tag를 한번 클릭해 해당 사이트를 방문한 뒤의 상태 표시에 사용
5. **`element:focus-within`**
= 자식 element에서 focused (키보드 선택) 시 focused-within으로 선택된 **부모 element에 적용
=** 부모 element 중 어느 하나라도 focused의 상태가 될 경우 부모 element에서 focused-within 발동(activated)
cf. within은 “안에”라는 의미를 갖는다.

> state문은 다른 state, 다른 pseudo selector와 함께 사용될 수 있다.
ex. `form:hover input:focused {}` = form이 hover된 상태에서 내부에 있는 input이 focused될 경우 input의 style 변경 (두 경우 모두 충족될 경우 해당 상황이 진행됨) 
      `form:hover input{}` = form이 hover된 상태에서 form 내부에 있는 input의 style을 변경
> 

### **추가 pseudo element ⇒ `::` 을 이용한 것들**

⇒ 실제 존재하는 element는 아니지만 스타일링을 할 수 있게 도와주는 것들

1. **`element::placeholder`**
    
    = placeholder style만을 변경하고 싶을 때 사용. 입력 글자는 변경 X
    
2. **`element::selection`**
    
    마우스로 드래그할 때 style을 변경하고 싶을 때 사용.
    (padding 등은 불가. 몇가지 속성만 사용 가능 / 사이트에 개성을 불어넣어줌)
    
3. `**element::first-letter**`
    
    가장 첫번째 문자의 style을 변경하고 싶을 때 사용
    

그 외에도 `element::first-line` 등이 있음

## Combinators

### element1 + 공백 + element2

- element1 안에 자식 element로 존재하는 element2를 선택하는 방법
element1은 father / element2는 children selector인 셈
⇒ 부모 안에 있는 자식에만 CSS를 적용할 수 있음
- 자식 element가 직접적인 부모-자식 관계를 갖지 않더라도 부모 element 내에 속하기만 하면 모두 적용된다.
- 부모 자식 관계는 여러개 가능하다.
element1 + 공백 + element2 + 공백 + element3 + …
ex. `header p span {}` =  header element에 있는 p element 내부의 span element 선택

### element1 + ‘>’ + element2

- element1의 **바로 밑** 자식인 element2를 선택 (직계 부모-자식 관계를 가질 경우)

### element1 + ‘+’ + element2

- element1 바로 다음으로 오는 element2를 선택 (**형제** 관계)
코드 상에서 element1 바로 밑에 element2가 오는 경우를 의미

### element1 + ‘~’ + element2

- element1의 다음으로 오는 element2를 선택
(형제 관계, 바로 다음에 오지 않아도 괜찮음)

### Attribute Selector ⇒ element[attr=”value”] {}

- attribute를 통해 어떤 것이든 선택할 수 있게 하는 선택자
- `input[type=”password”] {}` = input element 중 type이 password 인 모든 element를 선택
- `input[placeholder~=”name”] {}` = input element 중 placeholder에 name이 들어있는 모든 element를 선택
    
    ⇒ `**~=**` : contain (포함하다)의 의미
    
- 이와 같은 문자가 ~= 이외에도 태그와 속성별로 존재함
    1. `**^=**` = 접두사(prefixed)로 특정 문자를 포함하는 경우
    2. `**$=**` = 접미사(suffixed)로 특정 문자를 포함하는 경우
    
    그 외 `***=**` , `|=` 등 다양하게 존재함 
    ex. `a[href*=”example”] {}` = a element 중 href에 “example”이 들어간 모든 케이스 선택
          `a[href$=”.org”] {}` = a element 중 href에 “.org”로 끝나는 모든 케이스 선택
    

---

## colors & variables(변수)

colors들은 css에서 정말 중요하다.
변수 역시 정말 많이 사용한다. 변수는 값을 저장할 수 있게 해 나중에 사용할 수 있도록 한다. CSS를 프로그래밍 언어처럼 보이게 만들고, 프로그래밍 언어의 장점을 보여주는 역할

### colors (CSS에서 알아야 할 3가지 컬러 시스템)

1. hexadecimal color (16진수 컬러)
    
    컬러코드를 입력해서 사용
    
2. RGB 방식 (디자이너가 많이 사용하는 방식)
    
    속성값으로 **`rgb(n,n,n)`**과 같이 입력한다.
    
    - RGBA
    = 색과 투명도 (a, 알파, opacity)를 설정하는 방법
    = a의 범위는 0 ~ 1 사이에 해당한다.
    (0이 투명도가 높은 것 색감을 볼 수 없음 / 1은 투명도가 없는 것)
    ex. rgba(n, n, n, n)
3. 이름 입력

### variables (custom property)

**`:root`** element에 변수를 추가해서 사용

**`:root`** = 기본적으로 모든 document의 뿌리가 됨 (출발점의 역할)

```css
:root {
	--main-color: #fcce00;
}
p {
	background-color: var(--main-color);
}
```

- custom property 작성 방법
    
    = dash(-) 2개 다음에 변수명 선언 (변수명 사이에 공백이 있다면 dash로 연결)
       (빈 공간이 있으면 안된다)
    
- custom property 사용 방법
    
    = 사용하고자 하는 곳(속성값)에 var()을 입력
       소괄호 안에 변수명을 --부터 입력
    

---