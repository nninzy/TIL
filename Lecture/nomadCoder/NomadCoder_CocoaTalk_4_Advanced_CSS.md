# 코코아톡 4. Advanced CSS

강의처: 노마드코더

기록 날짜: 2023/04/09

세줄 요약: transition과 transform, animation / media query (반응형 디자인)

주제: CSS

- 지난 시간의 CSS 주제들
    
    Variable (Custom Property) / Color / State / Selector
    

- 이번 시간의 CSS 주제들
    
    Animation / Transformation / Transition 등
    
    “CSS는 CSS가 할 수 있는 부분에서 아주 심화되어 있다”
    

---

## transition

어떤 상태 (초기상태)에서 다른 상태(state 상태)로 가는 변화를 애니메이션화 (부드러운 움직임, 효과를 부여)하는 것

- state에 따라 바뀌는 속성을 보다 부드럽게 변화하는데 사용한다.
(급격한 변화를 원하지 않고 변화 속도를 조절하고 싶을 때)
⇒ state와 root에 모두 해당 속성이 있어야 한다.
- **transition은 state가 없는, 초기 상태의(root) element에 입력해야함**
    
    ⇒ state 설정에 있으면 state 상태를 벗어나면 transition없이 원 상태로 돌아간다.
    
- state 상태를 유지하면 transition 역시 유지된다.
반응을 멈출 경우 즉시 원래 상태로 돌아간다.
- 변화하는 부분 각각의 세부적인 transition 설정은 `,` 로 연결한다.
state 모든 속성에 대해서 효과를 주고 싶다면 `all` 을 사용한다.

- transition에 써야 하는 것들 (공백 구분)
    1. 어떤 것을 애니메이션화해서 변화하고 싶은가? **(변화하는 부분)**
    2. 얼마 동안 **(how long)** 변화하고 싶은가?
    3. **ease-in function**
    = 브라우저에게 애니메이션이 **어떻게 변할 것인지** 말해주는 부분
    = state 상태 초기부터 후반부까지의 속도를 결정
        
        [https://matthewlein.com/tools/ceaser](https://matthewlein.com/tools/ceaser)
        = 처음부터 끝까지 transition 효과 설정 원할때 사용
        
        - 대부분 ease-in, ease-out, ease-in-out 중 하나 사용할 것임
        - `cubic-bezier(n, n, n, n)`로 세부적으로 조정할 수도 있음
        (개발자 고유의 커브 속도, 애니메이션를 만들 수 있도록 함)
- 예시코드
    
    ```html
    <head>
    	<style>
    		a {
    			color: wheat;
    			background-color: tomato;
    			text-decoration: none;
    			padding: 3px 5px;
    			border-radius: 5px;
    			font-size: 55px;
    			transition: background-color 10s ease-in-out, color 5s ease-in-out;
    		}
    		a:hover {
    			color: tomato;
    			background-color: wheat;
    		}
    	</style>
    </head>
    <body>
    	<a href="#"> Go Home </a>
    </body>
    ```
    

## transformation

한 요소를 변형(transform)시킬 때 사용

- transform에 다른 속성값을 추가하고 싶으면 공백을 통해 구분하면 된다.
- transformation은 적용 element의 형제 (siblings)요소에는 영향을 주지 않는다.
일종의 3D transformation과 같기에 margin이나 padding이 적용되지 않고 형제 요소 위에 존재한다
- transition 등과 함꼐 같이 적용할 수 있다.
transformation을 state 가 포함된 selector의 property로 입력하면 됨
    - 예시코드
        
        ```css
        img {
        	transition: transform 5s ase-in-out;
        }
        img:hover {
        	transformation: rotateZ(90deg);
        }
        ```
        
    

- transform에 사용할 수 있는 속성값들
(예시 이외에도 많음)
    - rotate (회전) ⇒ `rotateX( )` `rotateY( )` `rotateZ( )`
    소괄호 내부에는 deg(degree, 각도)단위가 들어감
    X, Y, Z는 축을 의미. 축을 기준으로 얼마만큼 회전하는가를 의미함
    - scale (확대) ⇒ `scaleX()` `scaleY()` `scale(n,n)`
    소괄호 내부에는 단순 숫자만 들어가며 이는 배수를 의미함
    두개의 단위가 ,로 연결되어 들어갈 경우에는 x와 y에 각각 효과를 적용한 것을 의미
    - translate (이동) ⇒ `translateX()` `translateY()`
    소괄호 내부에는 px 등의 크기 단위가 들어감
    ⇒ 다른 요소의 box를 변형시키지 않고 원하는 요소를 이동시키기 위해서 사용한다.
    - skew (비스듬히 기울이기)
    
    > transform MDN을 검색해서 transform의 다양한 속성값 살펴보고 적용해보기
    > 

## animation

계속 재생되는, 원하는 만큼 만들고 재생시킬 수 있는 애니메이션 (transition은 state 상태 조건을 충족할때만 진행) 효과를 줄 때 사용

- animation 을 사용하는 방법
    1. 기본 포맷
        
        > `@keyframes` + `애니메이션 변수명` + `{}`
        각 요소는 공백으로 구분
        ex. `@keyframes superSexyCoinFlip {}`
        > 
    2. keyframes에 입력할 옵션 1. 변화할 효과의 지점 설정
        1. `from {} to {}` = 어느 한 지점부터(from) 다른 한 지점(to)까지의 애니메이션을 만들고 싶을 때
            - 각 내부에는 변화요소(transform)에 대한 속성값이 들어간다.
            속성값은 공백을 통해 다른 것을 추가할 수 있다.
            - transform 이외에도 border-radius, border-color 등 다른 속성도 들어갈 수는 있지만 transform으로 하는 것을 권장한다.
            모든 속성이 가능한 것은 아니다. 애니메이션 효과가 적용 안되는 것도 있음
            ⇒ 자주 사용할 가능성이 높은 속성 `opacity` (투명도, fade-in fade-out 효과 만들 수 있음)
        2. 0% {} 50% {} 100% {} = 지점을 3가지로 나눠 애니메이션을 만들 수 있음 (원 상태로 돌아가는 효과)
        10%, 25% 75% 등 원하는 만큼 단계를 더 나눌 수 있다.
    3. animation 효과를 적용할 selector 내부에 animation 속성을 추가하고,
    속성값에 `애니메이션 변수명` + `효과 유지시간` + `ease-in-function (효과 속도)`을 입력한다.
    각 요소는 공백으로 구분한다.
        - 속성값 마지막에 `infinite`를 입력할 경우 해당 효과 유지시간동안 재생 + 무한 반복한다.
    
    [https://animista.net/](https://animista.net/) = CSS animation 관련해서 효과들을 볼 수 있는 곳
    
    - 예시코드
        
        ```css
        @keyframes superSexyCoinFlip {
        	from {
        		transform: rotateX(0);
        	}
        	to {
        		transform: rotateX(360deg) translateY(100px);
        	}
        }
        img {
        	animation: superSexyCoinFlip 5s ease-in-out;
        }
        ```
        

## media query (반응형 디자인)

CSS만을 이용해서 웹사이트를 보고 있는 사용자의 스크린의 사이즈, 가로(landscape모드)&세로 방향을 알 수 있는 방법

- media query를 사용하는 방법
    
    > `@media` + `screen` + `and` + `( )` + `{ }`
    > 
    > - media가 print 시 (crtl + shift + p를 누를 경우 보이는 화면)브라우저 화면이라면 screen 대신 print를 입력한다.
    > screen과 print를 한번에 설정하고 싶을 경우 `,` 를 이용해 연결한다.
    >     
    >     and ( ) 는 반드시 필요한 조건이 아니며 `screen { }` 이나 `print { }`만으로도 사용 가능하다.
    >     
    > - 소괄호 안에는 화면의 조건에 해당하는 내용이 들어간다.
    > (조건이 참일 경우 중괄호 내부의 CSS 코드를 실행할 것. 반드시 변경할 element도 지정해줘야함)
    >     
    >     ⇒ 조건에 들어갈수 있는 것들
    >     
    >     = `min-width` / `max-width` 
    >        `min-device-width` / `max-device-width` (핸드폰에서만 적용되는 조건, 브라우저는 인식할 수 없음)
    >        `orientation:landscape` (가로모드) / `orientation: portrait` (세로 모드)
    >     
    >     = 이외에도 다양한 것들이 존재함 (MDN에서 확인할 것)
    >     ex. `max-width:600px` = 해당 스크린이 최대너비 600px를 넘기지 않는 조건에서
    >     
    >     - 코드 예시
    >         
    >         ```html
    >         <head>
    >         	<style>
    >         		@media screen and (orientation: landscape) { /* 스크린 화면에서 가로모드일 때*/
    >         			span {
    >         				display: none; /* span element를 보이지 않게한다*?
    >         			}
    >         		}
    >         	</style>
    >         </head>
    >         <body>
    >         	<span>Please flip your phone :( </span>
    >         </body>
    >         ```
    >         
    >     
    >     ⇒ 조건을 더 추가하고 싶다면 `and ( )`를 추가해 사용할 수 있다.
    >     ex. `@media screen and (min-width: 600px) and (max-width: 750px) { }`
    >     
    > - 중괄호 안에서는 selector + { } 가 들어가며, 해당 조건에서 선택자의 상황을 의미한다.
    > ex. `div {background-color: tomato;}` = div element의 배경색을 tomato로 유지한다.
- PC 브라우저 상에서 핸드폰 화면 테스트를 하는 방법
    
    브라우저 마우스 우 클릭 → 검사(inspect) → 검색창 왼쪽 상단 두번째 버튼 (Toggle device toolbar)
    
    핸드폰 화면 테스트 페이지에서 상단 바에는 핸드폰 기종별 화면 크기를 확인할 수 있으며 화면 회전시 상황도 확인 가능