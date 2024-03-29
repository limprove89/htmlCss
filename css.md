# CSS

프론트앤드에서 스타일링을 담당하는 CSS

- HTML
- CSS
- Java script

이 세가지는 웹 개발에 있어 가장 필수적인 요소이며, 모든 웹에 기본이 되는 기술이다. 이번 세션에서는 CSS를 정리해나가도록 하겠다.

___

## 문법

> 선택자 {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;속성 : 속성값;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;속성 : 속성값;  
}

### 속성과 값

```HTML
<div>HELLO</div>
```

```CSS
div {
    color : red;
    font-size : 20px;
    font-weight : bold;
}
    /* 글자색 : 빨강;
       글자크기 : 20px;
       글자두께 : 두껍게; */
```

### 주석처리

/* comment */

```CSS
/* HEADER SECTION */
header {
    color : ##FF0000;  /* color : red */
}
```

### 선언방식

- 인라인 방식 (div 태그 안 style 속성으로 지정)
- 내장 방식 (html header 부분에 입력)
- 링크 방식 (html이 css를 불러올때 / 병렬방식)
- @import 방식 (css가 css를 불러올때 / 직렬방식)

### 선택자

#### 기본 선택자

- 전체 선택자 (*)
- 태그 선택자 (태그 이름 (ex) div, h1, h2, li)
- class 선택자 (.class 이름 (ex).orange)
- id 선택자 (#id 이름 (ex)#orange)

#### 복합 선택자

- 일치 선택자 : E와 F 동시만족 *붙여서 작성한다. (span.orange / div.apple)
- 자식 선택자 : E > F E의 자식요소인 F를 선택 (ul > .orange)
- 후손(하위) 선택자 : E의 후손 요소 F를 선택 *띄어써서 작성한다. (span .orange / div.apple)
- 인접 형제 선택자 : E의 다음 형제 요소 F 하나만 선택 E + F (.orange + li)
- 일반 형제 선택자 : E의 다음 형제 요소 F 모두를 선택 E ~ F (.orange ~ li)

#### 가상 클래스 선택자 ( 클래스:가상클래스 선택자 )

> 효과의 자연스러운 적용을 위해 transition: 0.4s 적용 할 것

- HOVER -> E에 마우스(포인터)가 올라가 있는 동안에만 E 선택
- ACTIVE -> E를 마우스로 클릭하는 동안에만 E 선택
- FOCUS -> E가 포커스 된 동안에만 E 선택 (대화형 컨텐츠에서 사용 가능)

___

- first-child : 형제 요소 중 첫번째 요소라면 선택  

```CSS
.fruits li:first-child {
    color: red;
}
```

- last-child : 형제 요소 중 마지막 요소 선택

```CSS
.fruits li:last-child {
    color: red;
}
```

- nth-child : E가 형제 요소 중 n번째 요소라면 선택 (n은 0부터 해석)

```CSS
.fruits li:nth-child(n+3){
    color: red;
}
```

>주의사항  
.box-group p:first-child { }  
p를 만족하는 첫번째 자식요소로써 해석해야 한다.  
위 구문은 box-group 클래스 후손 중에 첫번째 자식 요소가 p태그임을 만족하는 지를 나타내며, p를 생략하면 box-group 클래스 후손 중 첫번째 자식 요소를 지칭한다.

- nth-of-type : E의 타입과 동일한 타입인 형제 요소 중 E가 n번째 요소라면 선택

```CSS
.fruits p:nth-of-type(1){
    color : red;
}
```

- 부정 선택자 : s가 아닌 E 선택 -> E:not(s)

___

#### 가상 요소 선택자

- ::before : 엘리먼트 앞부분에 오는 태그 선택자
- ::after : 엘리먼트 뒷부분에 오는 태그 선택자

>CSS 속성 content를 입력해주어야 동작한다.

```HTML
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
    <li>5</li>
    <li>6</li>
    <li>7</li>
</ul>
```

```CSS
ul li::before {
    content: "";
    width: 30px;
}
```

___

#### 속성 선택자 [Attr], [attr=value]

- 속성 attr을 포함한 요소 선택

>HTML의 속성은 Attribute, CSS의 속성은 Property라고 한다. 속성 선택자는 HTML 속성을 선택하는 역활의 선택자이다.

```HTML
<input type="text" value="ID" disabled>
```

```CSS
[disabled]{
    opacity: 0.2;
}

[type="text"]{
    opacity: 0.2;
}
```

#### 속성 선택자 \[Attr^=value], \[attr$=value]

- 속성 attr을 포함하며 속성 값이 value로 시작하는/끝나는 요소 선택

```HTML
<button class="btn-success">success</button>
<button class="btn-danger">danger</button>
```

```CSS
[class^="btn-"]{
    font-weight: bold;
}
[class$="danger"]{
    color : red;
}
```

___

#### CSS 상속 (inheritance)

- 보통 글자를 다루는 속성들이 상속이 된다.  
- font

  - font-size
  - font-weight
  - font-style
  - line-height
  - font-family
- color
- text-align
- letter-spacing
- etc...

> 강제 상속 : 상속되지 않는 속성 또한 속성의 값으로 inherit;를 입력하면 상속 가능하다. 이 경우 자식을 제외한 후손에는 적용되지 않으며, 모든 속성이 다 강제 상속이 적용되는 것은 아니다.

#### 우선순위

- 같은 요소가 여러 선언의 대상이 될 경우, 어떤 선언의 CSS 속성(property)을 우선 적용할지 결정하는 방법

1. 명시도 점수가 높은 선언이 우선 (명시도)
2. 점수가 같은 경우, 가장 마지막에 해석되는 선언이 우선 (선언 순서)
3. 명시도는 "상속"규칙보다 우선 (중요도)
4. !important가 적용된 선언 방식이 다른 모든 방식보다 우선 (중요도)

> !important : 무한대의 점수  
inline 선언 방식 : 1000pt  
id seletor : 100pt  
class selector : 10pt  
type(tag) selector : 1pt  
\*(universal) selector : 0pt  
CSS inheritance : 0pt

___

## CSS reset

- 브라우저에서 제공하는 스타일은 모두 통일화 되어있지 않다.  
그렇기 때문에 CSS 초기화가 필요하다.  
가장 편하게 사용하는 방법으로는 reset.css 파일을 링크해서 사용하는 방법!

> 초기화 CDN 파일은 link css 파일 중 최상단에 위치하도록 한다.

### Emmet 문법

- HTML/CSS를 더욱 편하게 작성할 수 있는 문법.
- CSS 선택자를 작성 후 Tab
- 대다수의 코드 에디터에 내장되어 있다.

___

### CSS 단위

#### px, %

- px는 상대적이지만 고정값으로 이해하는것이 좋다.
- %는 부모 요소를 기준으로 수치가 계산되어 적용된다.

#### em, rem

- em은 현재 자기 자신이 가진 폰트사이즈에 영향을 받는다. (상속받은 자신의 폰트사이즈!)
- rem은 최상위 요소 HTML이 가진 폰트사이즈에 영향을 받는다.

#### vw, vh

- vw(뷰포트)는 화면상 보이는 영역의 가로 사이즈 (100%를 기준으로 한다. 절반을 선택하려면 50vw;)
- vh는 화면상 보이는 영역의 세로 사이즈

#### vmin, vmax

- vmin은 뷰포트의 가로/세로 중 더욱 짧은 쪽을 기준으로 계산한다.
- vmax는 뷰포트의 가로/세로 중 긴 쪽을 기준으로 계산한다.

### CSS / 속성 - 박스 모델

- 기본적으로 속성값은 기본값인 auto;로 설정된다.

#### width, height

- 속성에 가로/세로를 나타낸다.

값 | 의미 | 기본값
:---: | :---: | :---:
auto | 브라우저가 너비를 계산 | auto
단위 | px, em, cm 등 단위로 지정 |

#### max-width, min-width, max-height, min-height

- 요소의 최대/최소 가로/세로 너비

#### margin

- 요소의 '외부(바깥)여백'을 지정(단축속성/개별속성)
- 음수값을 사용할 수 있습니다.
- % 지정시 부모 요소의 가로 사이즈의 % 값이 설정된다.

#### collapse (마진 중복)

- 마진의 특정 값들이 '중복'되어 합쳐지는 현상

1. 형제 요소들의 margin-top와 margin-bottom이 만났을 떄
2. 부모 요소의 margin-top과 자식 요소의 margin-top이 만났을 때
3. 부모 요소의 margin-bottom과 자식 요소의 margin-bottom이 만났을 때

마진 중복 계산법

- 마진 중복 현상이 발생시, 중복 값을 계산하는 방법

조건 | 요소A 마진 | 요소B 마진 | 계산법 | 중복값
:---: | :---: | :---: | :---: | :---:
둘 다 양수 | 30px | 10px | 더 큰 값으로 중복 | 30px
둘 다 음수 | -30px | -10px | 더 작은 값으로 중복 | -30px
각 각 양수/음수 | -30px | 10px | -30 + 10= -20 | -20px

#### padding

- 요소의 '내부(안쪽) 여백'을 지정

#### 크기 증가

- 추가된 padding 값만큼 요소의 크기가 커지는 현상
- 하지만 box-sizing: border-box; 설정 시 크기가 커지지 않고 자동 계산 된다!

#### border

- 요소의 테두리 선을 지정
- 두께/종류/색상을 지정
- border 는 요소에 크기에 추가가 된다. 따라서 box-sizing: border-box;를 적용 시 크기가 커지지 않고 자동 계산 된다!

#### box-sizing

- 요소의 크기 계산 기준을 지정
- content-box (기본값) / border-box가 존재한다.

#### display

- 요소의 박스 타입(유형)을 설정
- block / inline / inline-block / table / flex / none 등

#### overflow

- 요소의 크기 이상으로 내용(자식요소)이 넘쳤을 때, 내용의 보여짐을 제어한다.
- visible(기본값) / hidden / scroll / auto 등

#### opacity

- 요소의 투명도를 지정
- 숫자로 0과 1사이의 숫자를 지정
- opacity: 0;은 존재하지만 보여지지 않는 것 / display:none;은 존재하지 않는 것

___

### CSS / 속성 - 폰트

### font

- 글자 관련 속성들을 지정 (단축속성)
- font: 기울기 두께 크기(필수) / 줄높이 글꼴(필수);

#### font-style

- 글자의 스타일(기울기)를 지정
- normal / italic / oblique

#### font-weight

- 글자의 두께(가중치)를 지정
- normal / bold / bolder(상위 요소보다 더 두껍게) / lighter(상위 요소보다 더 얇게) / 숫자
- font-weight는 100 단위로 100~900까지 존재한다.

#### font-size

- 글자의 크기를 지정
- 단위 / % / xx-small / x-small / small / medium / large / x-large / xx-large / smaller / larger

#### line-height

- 줄 높이(줄 간격)을 지정
- normal / 숫자(요소 자체 글꼴 크기의 배수로 지정) / 단위 / %

#### font-family

- 글꼴(서체)를 지정
- 글꼴 이름(서체 후보)목록을 지정
- font-family: [글꼴후보1, 글꼴후보2, ...], 글꼴계열(필수);

계열 | 의미
--- | ---
serif | 바탕체 계열
san-serif | 고딕체 계열
monospace | 고정너비 (가로폭이 동등한) 글꼴 계열
cursive | 필기체 계열
fantasy | 장식 글꼴 계열

#### color / 색상표현법

- 문자의 색상을 지정

표현 | 의미 | 예시
--- | --- | ---
색상이름 | 브라우저에서 제공하는 색상의 이름 | red, blue
Hex 색상코드 | 16진수 색상 | #000000
RGB | 빛의 삼원색 | rgb(255, 255, 255)
RGBA | 빛의 삼원색, 투명도 | rgb(255, 255, 255, .5)
HSL | 색상,채도,명도 | hsl(120, 100%, 50%)
HSLA | 색상,채도,명도,투명도 | hsla(120, 100%, 50%, .3)

#### text-align

- 문자 정렬 방식을 지정
- left / right / center /justify (양쪽 맞춤: 두줄이상에서만 적용가능)

#### text-indent

- (첫번째 줄의) 들여쓰기를 지정
- 음수 값을 사용할 수 있다.
- 화면 상 출력을 하지 않지만 필요한 컨텐츠를 명시적으로 text-indent: -9999px;로 설정한다.

#### text-decoration

- 문자의 장식(line)을 설정
- none / underline / overline / line-through

#### letter-spacing, word-spacing

- 문자의 자간(글자 사이 간격)을 설정 / 단어 사이(띄어쓰기)의 간격을 지정
- normal / 단위

___

### CSS / 속성 - 띄움(정렬), 위치

#### float

- 요소를 좌우 방향으로 띄움 (수평 정렬)
- none / left / right
- float 속성이 적용된 요소의 주위로 다른. 요소들이 흐르게 되는데 이를 방지하기 위해 속성을 '해제'해야 한다.

1. 형제요소에 clear: (left,right,both) 추가하여 해제
2. 부모요소에 overfolw: (hidden,auto) 추가하여 해제
3. 부모요소에 clearfix 클래스 추가하여 해제 (추천!)

> inline 속성이라 하더라도 float 속성이 부여되면 block로 변화한다.

#### clear

- float 속성이 적용되지 않도록 지정(해제)
- left/right/both

#### position

- 요조의 위치 지정 방법의 유형(기준)을 설정
- 기준을 설정하고 top/bottom/left/right로 핸들링

값 | 의미 | 기본값
--- | --- | ---
static | 유형 없음/ 배치 불가능 | static
relative | 요소 자신을 기준으로 배치 |
absolute | 위치 상 부모 요소를 기준으로 배치 |
fixed | 브라우저(뷰포트)를 기준으로 배치 |
sticky | 스크롤 영역 기준으로 배치 |

- relative
  - 요소 자신을 기준으로 하기에 주변에 영향을 주고 받는다.

- absolute
  - 위치 상 부모 요소를 기준으로 이동한다.
    - 다만 부모 요소에도 position 속성의 값이 부여되어야 인식한다.

- fixed
  - 뷰표트(브라우저)를 기준으로 위치한다.
  - (쇼핑몰 배너등에 자주 사용)

- sticky (IE 사용불가)
  - 스크롤 영역 기준으로 배치
  - top/bottom/left/right 중 1개 이상 명시해줘야 동작
  - 쇼핑몰 헤더 로고 상단 배치에 이용 가능

> 요소 쌓임 순서?  
요소가 쌓여 있는 순서를 통해 어떤 요소가 사용자와 가깝게(더욱 위에) 있는지를 결정 (Z축)

1. static을 제외한 position 속성의 값이 있을 경우 가장 위에 쌓임
2. position이 모두 존재한다면 z-index 속성의 숫자 값이 높을 수록 위에 쌓임
3. position 속성의 값이 있고, z-index 속성의 숫자 값이 같다면, 'HTML'의 마지막 코드일 수록 위에 쌓임 (나중에 작성한 코드)

- display 수정
  - absolute, fixed 속성 값이 적용된 요소는 display 속성의 값이 대부분 block로 수정

#### z-index

- position이 지정된 요소의 '요소 쌓임' 정도를 설정
- static을 제외한 position 속성이 있을 경우에만 사용이 가능하다.

값|의미|기본값
:---:|:---:|:---:
auto|부모요소와 동일한 '요소 쌓임' 정도로 설정| auto
숫자|단위 없음, 숫자가 높을수록 위에 쌓임|

___

### CSS / 속성 - 배경

### background

- 요소의 배경을 설정 (단축속성)
- background: 색상 이미지경로 반복 위치 스크롤특성;

#### background-color

- 요소의 배경 색상을 지정 (개별속성)

값 | 의미 | 기본값
--- | --- | ---
색상 | 요소의 배경 색상 | transparent (투명)

#### background-image

- 요소의 배경에 하나 이상의 이미지를 삽입 (개별속성)
- 배경 이미지 삽입 시, 요소의 크기가 설정되어 있어야 배경 이미지가 노출된다.
- 하나 이상의 '다중 배경 이미지' 사용 시 ,로 구분해서 사용

#### background-repeat

- 배경 이미지의 반복을 설정
- repeat / repeat-x / repeat-y / no-repeat

#### background-position

- 배경 이미지의 위치를 지정
- top / bottom / left / right / center / % / 단위

#### background-attachment

- 요소가 스크롤 될 때 배경 이미지의 스크롤 여부 설정
- scroll / fixed / local
- fixed : 쇼핑몰에 한때 유행했던 main 이미지가 고정이 되어 스크롤 되는 형태!
- local : plusx style의 사이트 구성에 응용하기 좋겠음

#### background-size

- 배경 이미지의 크기를 지정
- auto / 단위 / cover / contain

___

### CSS / 속성 - 전환 & 변환

#### transitions (전환)

- CSS 속성의 시작과 끝을 지정(전환 효과)하여 중간 값을 애니메이션
- 바뀌기 전/후 중에 전상태에 입력하는 것이 일반적이다.
- transition-property / transition-duration / transition-timing-function / transition-delay

#### transition-property

- 전환 효과를 사용할 속성 이름을 설정

값 | 의미 | 기본값
--- | --- | ---
all | 모든 속성에 적용 | all
속성이름 | 전환 효과를 사용할 속성 이름

#### transition-duration

- 전환 효과의 지속시간을 설정

값 | 의미 | 기본값
--- | --- | ---
시간 | 전환 효과가 지속되는 시간 | 0s

#### transition-timing-function

- 타이밍 함수 (애니메이션 전환 효과를 계산하는 방법) 지정

값 | 의미 | 기본값
--- | --- | ---
ease | 빠르게-느리게 | ease
linear | 일정하게 |
ease-in | 느리게-빠르게 |
ease-out | 빠르게-느리게|
ease-in-out | 느리게-빠르게-느리게 |
cubic-bezier(n,n,n,n) | 자신만의 값을 정의(0~1) |
step(n) | n번 분할된 애니메이션 |

> Easing.net 참조

#### transition-delay

- 전환 효과가 몇 초 뒤에 시작할지 대기시간을 설정

값 | 의미 | 기본값
--- | --- | ---
시간 | 전환 효과의 대기 시간을 설정 | 0s

#### transform (변환)

- 요소의 변환 효과(변형)을 지정
- rotate / translate / skew / scale...
- 2D 속성과 3D 속성이 존재
- transform과 transition은 당연하지만 같이 사용된다.

#### transform 2D

- 이동 / 크기 / 회전 / 기울임 / 2차원 변환 효과 등이 있다.
- 배치를 하려면 position 속성이 낫지만, 계속되는 움직임에서는 transform 으로 처리하는것이 낫다.

#### transform 3D

- 이동 / 크기 / 회전 /원근법 / 3차원 변환 효과 등이 있다.
- perspecitive -> 원근감을 적용해서 확인하는 방법 (가장 앞에 위치해야 동작한다.)
- 2D의 이미지를 3D로 표현 가능하다.

#### transform-origin

- 요소 변환의 기준점을 설정
- X축, Y축. Z축 기본값 (50%, 50%, 0)
- Web은 기본적으로 x축은 오른쪽을 향하지만 y축은 하단을 향한다. 따라서 x축 0% 설정시 왼쪽 이미지 끝부분 y축 0% 설정시 윗쪽 이미지 끝부분을 나타낸다.

#### transform-style

- 3D 변환 요소의 자식 요소도 3D 변환을 사용할지 설정
- flat (기본값/사용하지 않음) / preserve-3d (사용함)
- 계속적인 사용시 지속적으로 부모 요소에 작성을 해야 한다.

#### perspective

- 하위 요소를 관찰하는 원근 거리를 설정
- perspective 함수와 속성은 차이가 있다.
  - perspective 속성은 적용 대상이 관찰 대상의 부모 요소이다.
  - perspective 함수는 적용 대상이 관찰 대상이다.

> perspective 속성은 관찰 대상의 부모(조상) 요소에 적용하여 하위 요소들을 관찰하는 원근 거리를 설정하며, transform: perspective() 변환 함수는 관찰 대상에 직접 적용하여 그 대상을 관찰하는 원근 거리를 설정한다.

#### perspective-origin

- 원근 거리의 기준점을 설정

#### backfave-visibility

- 3D 변환으로 회전된 요소의 뒷면 숨김을 설정
- visible / hidden 으로 구성된다.

#### matrix(a,b,c,d,e,f)

- 요소의 2차원 변환(Transforms) 효과를 지정
- scale(), skew(), translate() 그리고 rotate()를 지정

> 요소의 일반 변환(Transforms) 함수(2D,3D)를 사용하더라도 브라우저에 의해 matrix 함수로 계산되어 적용됩니다. (2D 변환 함수는 matrix로, 3D 변환 함수는 matrix3d로) 따라서 일반적인 경우에는 matrix가 아닌 일반 변환 함수로 사용하여도 된다.

### CSS / 속성 - 애니메이션 & 다단

#### 애니메이션

- 요소에 애니메이션을 설정/제어 (단축속성)

```CSS
animation: 애니메이션이름 지속시간 [타이밍함수 대기시간 반복횟수 반복방향 전후상태 재생/정지];

.box {
    width: 100px;
    height: 100px;
    background: tomato;
    animation: hello 2s linear infinite both;
}

@keyframes hello {
    0% {width: 200px;}
    100% {width: 50px;}
}
```

#### keyframes rules

- 2개 이상의 애니메이션 중간 상태(프레임)을 지정
- 반복횟수 무한 : infinite; / 재생 후 자연스러운 연결 재생 : alternate;

#### animation - name/uuration

- name: 규칙의 이름을 지정 / 기본값: none
- duration: 애니메이션의 지속 시간 설정 / 기본값: 0s

#### animation - timing-function/delay

- timing-function: 타이밍 함수 지정
- delay: 애니메이션의 대기 시간 설정 (음수가 허용됨)

#### animation - iteration-count/direction

- iteration-count: 애니메이션의 반복 횟수를 설정 / 숫자 or infinite(무한)
- direction: 애니메이션의 반복 방향을 설정 / normal, reverse, alternate(정방향에서 역방향으로 왕복 반복), alternate-reverse(역방향에서 정방향으로 왕복 반복)

#### animation-fill-mode

- 애니메이션의 전후 상태(위치)를 설정
- none(기본값): 기존 위치에서 시작 -> 애니메이션 시작 위치로 이동 -> 동작 -> 기존 위치에서 끝
- forwards: 기존 위치에서 시작 -> 애니메이션 시작 위치로 이동 -> 동작 -> 애니메이션 끝 위치에서 끝
- backwards: 애니메이션 시작 위치에서 시작 -> 동작 -> 기존 위치에서 끝
- both : 애니메이션 시작 위치에서 시작 -> 동작 -> 애니메이션 끝 위치에서 끝

#### animation-play-state

- 애니메이션의 재생과 정지를 설정
- running(기본값): 애니메이션을 동작 / paused: 애니메이션 동작을 정지
- 실무 사용에서는 가상요소 선택자, 가상클래스 선택자를 합쳐서 응용가능

```CSS
.box::before {
    content: "running";
    font-size: 20px;
    color: white;
    font-weight: 700;
}
.box:hover {
    animation-play-state: paused;
    background-color: dodgerblue;
}
.box:hover::before {
    content: "paused";
}
```

#### 다단 (multi-columns)

- 일반 블록 레이아웃을 확장하여 여러 텍스트 다단으로 쉽게 정리하며, 가독성을 확보한다.
- columns: 다단을 정의 {auto(기본값) / column-width / column-count}
- column-gap: 단과 단 사이의 간격 설정
- column-rule: 단과 단 사이의 구분 선을 지정

___

## CSS 레이아웃

- 초창기에는 HTML에 레이아웃을 그려나가기 어려웠음.
- table 코딩 -> position, float을 이용한 레이아웃으로 진화해왔지만 레이아웃에 특화된 속성이 아니기에 아쉬웠으며 복잡했다.
- 레이아웃을 전문적으로 다루는 기능이 생겨났으며 그것이 flex, grid 이다.

### Flex

- container (부모요소)
  - display
  - flex-flow (direction / wrap)
  - justify-content
  - align-content
  - align-items
- items (자식요소)
  - order
  - flex (grow/shrink/basis)
  - align-self

### container

- display 속성으로 container를 정의한다.
- display: flex -> block 특성의 flex container를 정의
- display: inline-flex -> inline 특성의 flex container를 정의

> 컨테이너 자체에 적용되며, items에는 영향을 미치지 않는다.

#### flex-flow

- direction / wrap 의 단축속성이다.
- flex-direction -> items의 주 축을 설정 (row/row-reverse/column/column-reverse)
- flex-wrap -> items의 여러 줄 묶음 설정 (nowrap/wrap/wrap-reverse)

#### justify-content

- 주 축의 정렬 방법을 설정한다.
- flex-start / flex-end / center / space-between / space-around  

![flex-justify-content](https://heropy.blog/images/screenshot/flex-justify-content.jpg)

#### align-content

- 교차 축의 정렬 방법을 설정
- flex-wrap을 통해 items가 2줄 이상이며, 여백이 있을 경우에만 사용가능
- stretch / flex-start / flex-end / center / space-between / space-around

![flex-align-content](https://heropy.blog/images/screenshot/flex-align-content.jpg)

#### align-items

- 교차 축에서 items의 정렬 방법을 설정
- items가 한 줄일 경우에 사용 -> (2줄일 경우에는) align-content: stretch(기본값)일때 설정 해야한다.
- stretch / flex-start / flex-end / center / baseline

![flex-align-items](https://heropy.blog/images/screenshot/flex-align-items.jpg)

### items

#### order

- item의 순서를 설정
- item에 숫자가 클수록 순서가 밀리며, 음수를 허용.
- order: 순서;

![flex-item-order](https://heropy.blog/images/screenshot/flex-order.jpg)

#### grow

- item의 증가 너비 비율을 설정
- 숫자가 크면 더 많은 너비를 가지며, item이 가변 너비가 아니거나, 값이 0일 경우 효과가 없다.
- flex-grow: 증가너비;

![flex-frow](https://heropy.blog/images/screenshot/flex-grow.jpg)

#### shrink

- item이 감소하는 너비의 비율을 설정
- 숫자가 크면 더 많은 너비가 감소되며, item이 가변 너비가 아니거나, 값이 0일 경우 효과가 없다.
- flex-shrink: 감소너비;

![flex-shrink](https://heropy.blog/images/screenshot/flex-shrink.jpg)

#### basis

- item의 (공간 배분 전) 기본 너비를 설정
- 값이 auto일 경우 width, height 등의 속성으로 item의 너비를 설정할 수 있다.
- 하지만 단위(px,em,cm)값이 주어진 경우 설정할 수 없다.
- flex-basis : 기본너비;

![flex-basis](https://heropy.blog/images/screenshot/flex-basis.jpg)

#### flex (grow / shrink / basis)

- item의 너비 (증가,감소,기본)를 설정하는 단축속성입니다.
- 주의할 점은 flex 단축 속성 사용시 basis의 기본값은 auto가 아닌 0으로 설정된다.
- flex: 증가너비 감소너비 기본너비;

#### align-self

- 교차 축에서 개별 item의 정렬 방법을 설정
- align-ltems는 container에 적용 방법을 설정하며, 필요에 의해 일부 item만 정렬 방법을 변경할때 align-self를 사용
- 이 속성은 align-items 보다 우선시 된다.
- align-self: 정렬방법;

![flex-align-self](https://heropy.blog/images/screenshot/flex-align-self.jpg)

___

### grid

- grid는 2차원 (행과 열)의 레이아웃 시스템
- 1차원적인 flex 보다 복잡한 레이아웃 구성을 위해 사용
- container
  - display
  - template (rows / columns / areas)
  - auto (rows / columns / flow)
  - grid (grid-template / grid-auto)
  - gap (row-gap / column-gap)
  - align-content
  - justify-content
  - place-content
  - align-ltems
  - justify-items
  - place-items
- item
  - row (row-start / row-end)
  - column (column-start / column-end)
  - area
  - align-self
  - justify-self
  - place-self
  - order
  - z-index

### display

- grid container를 정의한다.
- 정의한 컨테이너의 자식요소는 자동적으로 items으로 정의된다
- grid / inline-grid
- .container { display: grid;}

#### template (rows / columns)

- 명시적으로 행/열의 크기를 정의한다.
- fr (fraction, 공간 비율) 단위를 사용할 수 있다.
- repeat() 함수를 사용할 수 있다.
- 크기 정의 사이에 라인의 이름도 정의할 수 있다 []안에 이름 기입
- 라인 시작번호/끝 번호 로 공간을 정의할 수 있다.
- .container {  
display: grid;  
grid-template-rows: 100px 1fr;  
grid-template-columns : repeat(3, 1fr);  
grid-template-rows: [first] 100px [second] 1fr [third];  
grid-template-columns : repeat(3, 1fr);  
}
- grid-template 단축 속성으로 area로 정의된 공간들 배치와 크기 까지 한번에 작성 가능

```CSS
.container {
  display: grid;
  grid-template:
    "header header header" 80px
    "main main aside" 350px
    "footer footer footer" 130px
    / 2fr 100px 1fr;
}
header { grid-area: header; }
main   { grid-area: main; }
aside  { grid-area: aside; }
footer { grid-area: footer; }
```

#### template-areas

- 지정된 그리드 영역 이름(item에 적용한 grid-area)을 참조해 그리드 템플릿을 구성
- container가 아닌 item에 grid-area를 사용해 이름을 정의해 주고 그 이름을 가지고 템플릿을 구성.

```CSS
.container {
  display: grid;
  grid-template-rows: repeat(4, 100px);
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    "header header header"
    "main . ."
    "main . aside"
    "footer footer footer";
}
header { grid-area: header; }
main   { grid-area: main;   }
aside  { grid-area: aside;  }
footer { grid-area: footer; }
```

#### row-gap / column-gap

- 각 행과 행 / 열과 열 사이의 간격을 지정.
- gap: <grid-row-gap> <grid-column-gap>;

#### auto (rows / columns)

- 암시적 행/열의 크기를 정의
- container에 정의한 명시적 행을 item의 정의로 인해 벗어나게 되는 경우 암시적인 행/열의 크기가 적용됨

```HTML
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

```CSS
.container {
  width: 300px;
  height: 200px;
  display: grid;
  grid-template-rows: 100px 100px; /* 명시적 2개 행 정의 */
  grid-template-columns: 150px 150px; /* 명시적 2개 열 정의 */
  grid-auto-rows: 100px; /* 그 외(암시적) 행의 크기 정의 */
}
.item:nth-child(3) {
  grid-row: 3 / 4;
}
```

![grid-auto-rows](https://heropy.blog/images/screenshot/css-grid/grid-auto-rows-1.jpg)
![grid-auto-columns](https://heropy.blog/images/screenshot/css-grid/grid-auto-columns-1.jpg)
![grid-auto-columns](https://heropy.blog/images/screenshot/css-grid/grid-auto-columns-2.jpg)

#### auto-flow

- 배치하지 않은 아이템(item)을 어떤 방식의 '자동 배치 알고리즘'으로 처리할 지 정의
- 배치 한 아이템은 grid-area 를 사용한 아이템을 의미
- row / column / row dense (빈 영역 채움) / column dense (빈 영역 채움)

![grid-auto-flow](https://heropy.blog/images/screenshot/css-grid/grid-auto-flow-1.jpg)
![grid-auto-flow](https://heropy.blog/images/screenshot/css-grid/grid-auto-flow-2.jpg)

#### align-content / justify-content

- 그리드 컨텐츠(전체영역)를 수직/수평 정렬

![align-content](https://heropy.blog/images/screenshot/css-grid/align-content-1.jpg)
![justify-content](https://heropy.blog/images/screenshot/css-grid/justify-content-1.jpg)

#### align-items / justify-items

- 그리드 아이템의(각각) 수직/수평 정렬
![align-items](https://heropy.blog/images/screenshot/css-grid/align-items-1.jpg)
![justify-items](https://heropy.blog/images/screenshot/css-grid/justify-items-1.jpg)

___

### items

#### row / column

- items에 적용되는 속성은 대부분 단수형
- 각각 item에 배치 설정
- span은 그 수만큼 확장하라는 의미
- /를 기준으로 앞은 row(column)-start, 뒤는 row(column)-end를 의미
- grid-row: 1 / 3;
- grid-column: 1 / 4;

#### area

- container에서 나온 바와같이 공간에 이름을 정의할 때 사용
- 또한 grid-row(column)-start(end)의 단축 속성으로도 사용
- 영역 이름을 설정할 경우 row/column 개념은 무시된다.
- 또한 주의할 문법으로는 시작 / 시작 / 끝 / 끝 으로 작성한다.
  - grid-area: \<grid-row-start> / \<grid-column-start> / \<grid-row-end> / \<grid-column-end>;

#### align-self, justify-self

- 단일 그리드 아이템에 수직(수평)을 정렬한다.

![align-self](https://heropy.blog/images/screenshot/css-grid/align-self-1.jpg)
![justify-self](https://heropy.blog/images/screenshot/css-grid/justify-self-1.jpg)

#### order

- 그리드 아이템이 자동 배치되는 순서를 변경할 수 있다,
- 숫자가 작을수록 앞에 배치된다.

#### z-index

- z-index 속성을 이용해 아이템이 쌓이는 순서를 변경할 수 있다.

![grid-item-z-index](https://heropy.blog/images/screenshot/css-grid/z-index-1.jpg)

### grid functions

#### repeat

- 반복되는 횟수의 행/열의 크기를 정의
- 첫번째 인수로는 '반복 횟수' 두번째 인수로는 '행/열의 크기'

```HTML
/* 9컬럼 그리드 */
.container {
  grid-template-columns: 100px 100px 100px 100px 100px 100px 100px 100px 100px;
}
.container {
  grid-template-columns: repeat(9, 100px);
}
.container {
  grid-template-rows: [row-start] 200px [row-end row-start] 200px [row-end];
  grid-template-columns: [col-start] 100px [col-end col-start] 100px [col-end col-start] 100px [col-end];
}
.container {
  grid-template-rows: repeat(2, [row-start] 200px [row-end]);
  grid-template-columns: repeat(3, [col-start] 100px [col-end]);
}
.container {
  grid-template: repeat(2, [row-start] 200px [row-end]) / repeat(3, [col-start] 100px [col-end]);
}
.container {
  /* 12컬럼 그리드 */
  grid-template-columns: 1fr 2fr 1fr 2fr 1fr 2fr 1fr 2fr 1fr 2fr 1fr 2fr;
}
.container {
  grid-template-columns: repeat(6, 1fr 2fr);
```

#### minmax

- 행/열의 '최소/최대 크기'를 정의
- 첫번째 인수는 '최소값' 두번째 인수는 '최대값'
- auto를 사용하면 유연하게 크기를 지정할 수 있다.

```HTML
.container {
  grid-template-columns: minmax(100px, 1fr) minmax(200px, 1fr);
}
```

![minmax](https://heropy.blog/images/screenshot/css-grid/minmax-1.jpg)

#### fit-content

- 행/열의 크기를 그리드 아이템이 포함하는 내용(컨텐츠)에 맞춤
- 내용의 최댓값을 인수로 사용한다.
- 컨텐츠의 크기를 사용하되 최대 (인숫값)으로 설정하는 의미

```HTML
.container {
  grid-template-columns: fit-content(300px) fit-content(300px);
}
```

![minmax](https://heropy.blog/images/screenshot/css-grid/fit-content-1.jpg)

### grid units (그리드 단위)

#### fr(fractional unit)

- 사용 가능한 공간에 대한 비율

#### min-content

- grid-item이 포함하는 내용의 최소 크기
- 한글 사용시 음절로 나누어질때는
  - word-break: keep-all;

#### max-content

- grid-item이 포함하는 내용의 최대 크기

#### auto-fill / auto-fit

- 행/열의 개수를 컨테이너 행/열 크기에 맞게 자동적으로 조정
- repeat() 함수와 같이 사용하며, 행/열과 아이템 개수가 명확하지 않은 경우 사용
- 기본적으로 동일하나, fill은 남은 공간을 놔두고 fit은 남은 공간을 채우는 개념

```HTML
.container {
  grid-template-columns: repeat(4, minmax(120px, 1fr));
}
```

![auto-fill](https://heropy.blog/images/screenshot/css-grid/auto-fill-1.jpg)

```HTML
.container {
  grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
}
```

![auto-fill](https://heropy.blog/images/screenshot/css-grid/auto-fill-2.jpg)

```HTML
.container.auto-fill {
  grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
}
.container.auto-fit {
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
}
```

![auto-fit](https://heropy.blog/images/screenshot/css-grid/auto-fill-3.jpg)