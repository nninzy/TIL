# 코코아톡 1. Introduction

강의처: 노마드코더

기록 날짜: 2023/04/03

세줄 요약: 브라우저 내 언어의 종류 / 각 언어의 역할

작성 완료: Yes

주제: FE

### 수업을 위해 필요한 것

1. Browser → “구글 크롬” (또는 Brave = Google Chrome + Ad-blocker)
2. text editor (코드 수정기) → “Visual Studio Code”
3. Github Desktop

### 브라우저 (웹사이트)에 대한 이해

웹사이트는 가장 단순한 형태 (언론사 뉴스)만을 갖췄을 수도 인터렉티브할 수도 있다.

웹사이트의 구조를 알 수 있는 방법 > “개발자 도구” (view - developer - view resourse)

<aside>
💡 **Website Is Just Text File**
얼마나 단순하건, 복잡한 형태건 상관없이 text의 형태이다.
우리가 맞는 장소에 text를 쓴다면 우리도 웹 사이트를 만들 수 있다.

</aside>

텍스트 파일을 웹사이트로 만들어 주는 것 = 브라우저
**브라우저는 내가 쓴 코드를 이해하고, 생생한 웹사이트로 구현해주는 역할을 한다.**

우리는 어떤 종류의 text를 써야 하고, text를 어디에 써야하는지 알아야 한다.

**브라우저에 있는 text의 종류 (브라우저가 이해하는 언어들 - 최소 2, 최대 3)
    1. HTML ( for content structure )**

    **2. CSS ( for design )**                      

    **3. Javascript ( for interactivity )**
    그 외의 언어는 필요하지 않다.
    이중 CSS는 끊임없이 연습해야하고 (어렵진 않음), Javascript는 따로 공부해야함.

---

### What is HTML (웹 사이트의 뼈대)

- Hyper Text Markup Language의 약자

<aside>
💡 브라우저는 인간이 쓰는 언어를 이해하지 못한다.
웹 사이트 내에 있는 우리의 content를 이해하지 못하기에, 각 콘텐츠(title, image, sidebar 등)를 알려줘야함
By HTML

</aside>

- HTML의 역할 - 브라우저에게 콘텐츠의 구조가 어떤지(콘텐츠가 어떻게 구성되어 있는지) 설명해주는 것
(”What is the content of the website”)

### What is CSS (웹 사이트의 근육)

- Cascading Style Sheets의 약자
- HTML과 같이 써야한다 (CSS나 HTML 둘 중 하나만을 사용하지 않는다)
HTML이 없으면 CSS는 아무것도 디자인할 수 없음
CSS가 없으면 HTML은 예뻐보이지 않음 (단독 사용가능하나 의미가 없음)
- CSS는 브라우저에게 웹사이트가 어떻게 보여야하는지 설명해주는 것
(”How does the content Looks Like”)
HTML이 알려준 content의 디자인을 지정해주는 역할 (콘텐츠의 공백, 위치, 크기, 색상 등)

### What is Javascript (웹사이트의 뇌)

- 웹사이트에 동적인 기능(애니메이션, loader,bar 등)을 추가하는 역할

<aside>
💡 동적 상호작용성 (interactivity)
- 뭔가를 클릭하면 어떤 일이 생기는 반응 (connection)
- Javascript가 웹 사이트에서 하는 역할
- animation, transformation, 브라우저 크기에 따른 responsive 등은 Javscript 없이 가능하지만
  그 이상의 것들을 하기 위해서는 Javascript가 필요함

</aside>

---

<aside>
💡 **Recap**

- HTML (웹사이트의 뼈)
브라우저에게 웹사이트에 어떤 콘텐츠가 있는지 알려줌 (웹사이트 내 콘텐츠 구조 잡아줌)
프로그래밍 언어가 아님 (Markup Language. Markup은 content를 의미함)
- CSS (웹사이트의 근육)
브라우저에게 HTML이 알려준 content들이 어떻게 보여야 하는지 알려줌
프로그래밍 언어가 아님 (디자인과 스타일을 위한 언어)
- Javascript (웹사이트의 뇌)
웹사이트를 동적으로 만들어줌 (Click후 나타나는 반응들을 설정해줌)
프로그래밍 언어이자, 유일한 웹 프로그래밍 언어
</aside>