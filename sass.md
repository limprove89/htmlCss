# Sass

CSS Preprocessor : CSS 전(예비) 처리기

CSS는 상대적으로 low하며 raw한 문법이다. 프로젝트의 크기가 커질수록 불필요한 반복 작업들이 늘어난다.
하지만 웹에서 동작하는 HTML의 스타일을 입히는 언어는 CSS가 유일하다. 따라서 Sass는 직접적으로 웹에 적용되지 않고 컴파일 단계를 거친다.

전처리라는 것은 CSS로 변환되기 전에 작성되기에 전(예비)처리라고 하며, Less, Sass(SCSS), Stylus가 대표적이다.

## Sass와 SCSS의 차이

- Sass(Syntactically Awesome Style Sheets)의 3버전에서 새롭게 등장한 SCSS는 CSS 구문과 완전히 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능을 지원하는 CSS의 상위집합 (Superset)이다.  
즉, SCSS는 CSS와 거의 같은 문법으로 Sass 기능을 지원한다.
- 쉽고 간단한 차이는 {} (중괄호)와 ;(세미콜론)의 유무 / Mixins(믹스인) 방식의 차이 등이 있다.

## 컴파일

Sass(SCSS)는 웹에서 직접 동작할 수 없다.  
컴파일의 과정이 필수이며 대표적인 컴파일러로는

- SassMeister
  - 실시간 웹 컨파일러  
  - 사용시 Option에서 Syntax와 Compiler를 설정하고 사용해야 한다.

- Parcel

  - Parcel은 웹 애플리케이션 번들러로 단순하게 컴파일이 가능하다.  
  - node js 환경에서 사용하므로 npm을 이용하여 설치하고 사용한다.

## 문법

### 주석

- /* */ (컴파일 되는 주석)
  - Sass의 경우 맨 앞에 라인을 맞춰 *를 작성하여준다.
- // (컴파일 되지 않는 주석)

### 데이터 종류 (Data Types)

데이터 | 설명 | 예시
--- | --- | ---
Numbers | 숫자 | 1, 82, 20px
Strings | 문자 | bold, relative
Colors | 색상 표현 | red, #FFFF00
Booleans | 논리 | true, false
Nulls | 아무것도 없음 | null
Lists | 공백이나 ,로 구분된 값의 목록 | (apple, orange), apple orange
Maps | Lists와 유사하나 값이 Key:value 형태 | (apple:a, banana:b)

#### 특이사항

- Numbers: 숫자에 단위가 있거나 없다.
- Strings: 문자에 따옴표가 있거나 없다.
- Nulls: 속성값으로 null이 사용되면 컴파일하지 않는다.
- List: ()를 붙이거나 붙이지 않는다.
- Maps: ()를 꼭 붙여야 한다.

### 중첩

Sass는 중첩 기능을 사용할 수 있다.  
상위 선택자의 반복을 피하고 좀 더 편리하게 복잡한 구조를 작성할 수 있다.

```SCSS
.section {
    width: 100%;
    .list {
        padding: 20px;
        li {
            float: left;
        }
    }
}

/* complied to */
.section {
    width: 100%;
}
.section .list {
    padding: 20px;
}
.section .list li {
    float: left;
}
```

#### Ampersand (상위 선택자 참조)

중첩 안에서 & 키워드는 상위(부모) 선택자를 참조하여 치환된다.  
&로 기입하지 않으면 후손에 같은 클래스가 있다고 인식하여 오류를 발생시킨다.

```SCSS
.btn {
    position: absolute;
    &.active {
        color: red;
    }
}

.list {
    li {
        &:last-child {
            margin-right: 0;
        }
    }
}

/* compiled to */
.btn {
    position: absolute;
}
.btn.active {
    color: red;
}
.list li:last-child {
    margin-right: 0;
}
```

#### @at-root (중첩 벗어나기)

중첩에서 벗어나고 싶을 때 @at-root 키워드를 사용한다.  
중첩 안에서 생성하되 중첩 밖에서 사용해야 경우에 유용하다.

```SCSS
.list {
    $w: 100px;
    $h: 50px;
    li {
        width: $w;
        height: $h;
    }
    @at-root .box {
        width: $w;
        height: $h;
    }
}

/* compiled to */
.list li {
    width: 100px;
    height: 50px;
}
.box {
    width: 100px;
    height: 50px;
}

```

#### 중첩된 속성 정의

font-, margin- 등과 같이 동일한 네임 스페이스를 가지는 속성들을 다음과 같이 사용

```SCSS
.box {
    font: {
        weight: bold;
        size: 10px;
        family: sans-serif;
    };
    margin: {
        top: 10px;
        left: 20px;
    };
    padding: {
        bottom: 40px;
        right: 30px;
    };
}

/* compiled to */
.box {
    font-weight: bold;
    font-size: 10px;
    font-family: sans-serif;
    margin-top: 10px;
    margin-left: 20px;
    padding-bottom: 40px;
    padding-right: 30px;
}
```

### 변수

반복적으로 사용되는 값을 변수로 지정할 수 있다.  
변수 이름 앞에는 항상 $을 붙인다.

> $변수이름: 속성값;

```SCSS
$color-primary: #e96900;
$url-images: "/assets/images/";
$w : 200px;

.box {
    width: $w;
    margin-left: $w;
    background: $color-primary url($url-images + "bg.jpg");
}

/* compiled to */
.box {
  width: 200px;
  margin-left: 200px;
  background: #e96900 url("/assets/images/bg.jpg");
}
```

#### 변수 유효범위

변수는 사용 가능한 유효범위가 있다.  
선언된 블록 {} 내에서만 유효범위를 가진다.  

변수 $color는 .box1 의 블록 안에서 설정되었기 때문에, 블록 밖에 .box2 에서는 사용할 수 없다.

```SCSS
.box1 {
    $color: #111;
    background: $color;
}

/* Erorr */
.box2 {
    background: $color;
}
```

#### 변수 재 할당

변수를 다른 변수에 재 할당 가능하다.

```SCSS
$red: #FF0000;
$blue: #0000FF;

$color-primary: $blue;
$color-danger: $red;

.box {
    color: $color-primary;
    background: $color-danger;
}

/* compiled to */
.box {
    color: #0000FF;
    background: #FF0000;
}
```

#### 변수 전역 설정 (!global)

!global 플래그를 사용하면 변수의 유효범위를 전역으로 설정 가능하다.

```SCSS
.box1 {
    $color: #111 !global;
    background: $color;
}
.box2 {
    background: $color;
}

/* compiled to */
.box1 {
    color: #111;
}
.box2 {
    color: #111;
}
```

#### 변수의 초기값 설정 (!default)

!defaule 플래그는 할당되지 않은 변수의 초기값을 설정한다.  
즉, 할당되어 있는 변수가 있다면 그 변수의 기존 할당 값을 사용하도록 한다. (변수와 값을 설정하겠지만, 기존 변수가 있을 경우 현재 설장하는 변수의 값은 사용하지 않겠다는 의미)

```SCSS
$color-primary: red;

.box {
    $color-primary: blue !defaule;
    background: $color-primary;
}

/* compiled to */
.box {
    color: red;
}
```

#### 문자 보간 (#{})

\#{} 를 이용하여 코드의 어디든지 변수 값을 넣을 수 있다.  
Sass의 내장 함수 unquote()는 문자에서 따옴표를 제거한다.

```SCSS
$family: unquote("Droid+sans");
@import url("http://fonts.googleapis.com/css?family=#{$family}");

/* compiled to */
@import url("http://fonts.googleapis.com/css?family=Droid+Sans");
```

### 가져오기

@import로 외부에서 가져온 Sass 파일은 모두 단일 CSS 출력 파일로 병합된다.  
또한, 가져온 파일에 정의된 모든 변수 또는 Mixins 등을 주 파일에서 사용할 수 있다.  

Sass @import는 기본적으로 Sass 파일을 가져오는데, CSS @import 규칙으로 컴파일되는 몇 가지 상황이 있다.

- 파일 확장자가 .css 일 경우
- 파일 이름이 <http://>로 시작하는 경우
- url()이 붙었을 경우
- 미디어쿼리가 있는 경우

위의 경우 CSS @import 규칙대로 컴파일 된다.

#### 여러 파일 가져오기

하나의 @improt로 여러 파일을 가져올 수 있다.  
파일 이름은 ,로 구분한다.

```SCSS
@import "header", "footer";
```

#### 파일 분할 (Partials)

프로젝트가 커지면 파일들을 header 나 side-menu 같이 각 기능과 부분으로 나눠 유지보수가 쉽도록 관리하게 된다.  
이 경우 파일의 수가 점점 많아지는데, 모든 파일이 컴파일 시 각각의 ~.css 파일로 나눠서 저장된다면 관리나 성능 차원에 문제가 발생한다. 그래서 Sass는 Partials 기능을 지원한다.  
파일 이름 앞에 _를 붙여 (_header.scss와 같이) @import로 가져오면 컴파일 시 ~.css로 컴파일되지 않는다.  

```SCSS
Sass-App
  # ...
  ├─scss
  │  ├─header.scss
  │  ├─side-menu.scss
  │  └─main.scss
  # ...
// main.scss
@import "header", "side-menu";

/* compiled to */
  Sass-App
  # ...
  ├─css
  │  ├─header.css
  │  ├─side-menu.css
  │  └─main.css
  ├─scss
  │  ├─header.scss
  │  ├─side-menu.scss
  │  └─main.scss
  # ...

Sass-App
  # ...
  ├─scss
  │  ├─_header.scss
  │  ├─_side-menu.scss
  │  └─main.scss
  # ...  
// main.scss
@import "header", "side-menu";
/* compiled to */
Sass-App
  # ...
  ├─css
  │  └─main.css  # main + header + side-menu
  ├─scss
  │  ├─header.scss
  │  ├─side-menu.scss
  │  └─main.scss
  # ...
  ```

### 연산

Sass는 기본적인 연산을 지원한다.  
레이아웃 작업시 상황에 맞게 크기를 계산하거나 정해진 값을 나눠서 작성할 경우 유용하다.

산술 연산자  

종류 | 설명 | 주의사항
--- | --- | ---
\+ | 더하기 |
\- | 빼기 |
\* | 곱하기 | 하나 이상의 값이 반드시 숫자(Number)
\/ | 나누기 | 오른쪽 값이 반드시 숫자(Number)
\% | 나머지 |

비교 연산자

종류 | 설명
--- | ---
== | 동등
!= | 부등
\< | 대소 / 보다 작은
\> | 대소 / 보다 큰
<= | 대소 및 동등 / 보다 작거나 같은
\>= | 대소 및 동등 / 보다 크거나 같은

논리 연산자

종류 | 설명
--- | ---
and | 그리고
or | 또는
not | 부정

#### 숫자

##### 상대적 단위 연산

일반적으로 절댓값을 나타내는 px 단위로 연산을 하지만, 상대적 단위(%, em, vw 등)의 연산의 경우 CSS calc()로 연산해야 한다.

```SCSS
width: 50% - 20px;  // 단위 모순 에러(Incompatible units error)
width: calc(50% - 20px);  // 연산 가능
```

##### 나누기 연산의 주의사항

CSS는 속성 값의 숫자를 분리하는 방법으로 /를 허용하기 때문에 /가 나누기 연산으로 사용되지 않을 수 있다. 예를 들어, font: 16px / 22px serif; 는 font-size: 16px과 line-height: 22px의 속성값 분리를 위해 /를 사용한다. 따라서 나누기 연산은 주의사항이 필요하다.

```SCSS
div {
    width: 20px + 20px;
    height: 40px - 10px;
    font-size: 10px * 2;
    margin: 30px / 2;
}

/* compiled to */
div {
    width: 40px;
    height: 30px;
    font-size: 20px;
    margin: 30px / 2;
}
```

나누기 연산 시 다음 조건을 충족해야 한다.

- 값 또는 그 일부가 변수에 저장되거나 함수에 의해 반환되는 경우
- 값이 ()로 묶여있는 경우
- 값이 다른 산술 표현식의 일부로 사용되는 경우

```SCSS
div {
    $x: 100px;
    width: $x /2;
    height: (100px / 2);
    font-size: 10px + 12px / 3;
}

/* compiled to */
div {
    width: 50px;
    height: 50px;
    font-size: 14px;
}
```

#### 문자

문자 연산에는 +가 사용된다.  
문자 연산의 결과는 첫 번째 피연산자를 기준으로 한다.  
첫번째 피연산자에 ''가 붙으면 전체에 ''를 붙여 출력하며, 첫번째 피연산자에 ''가 없으면 전체에 ''를 처리하지 않고 반환한다.

```SCSS
div::after {
    content: "Hello" + world;
    flex-flow: row + "-reverse" + " " +wrap;
}

/* compiled to */
div::after {
    content: "Hello world";
    flex-flow: row-reverse wrap;
}
```

#### 색상

색상도 연산이 가능 (#는 16진수로 연산/ rgba에서는 alpha값이 같아야 연산 가능)

```SCSS
div {
    color: #123456 + #345678;
    // R : 12 + 34 = 46
    // G : 34 + 56 = 8a
    // B : 56 + 78 = ce
    background: rgba(50, 100, 150, 0.5) + rgba(10, 20, 30, 0.5);
    // R : 50 + 10 = 60
    // G : 100 + 20 = 120
    // B : 150 + 30 = 180
    // A : Alpha channels must be equal
}

/*compiled to */
div {
    color : #468ace;
    background: rgba(60, 120, 180, 0.5);
}
```

RGBA에서 Alpha값(투명도)의 값이 동일하여야 연산 가능하며, 연산을 하여야 하는 경우에는 opacify(), transparentize() 함수를 사용하여 연산 가능하다.

#### 논리

Sass의 @if 조건문에서 사용되는 논리(Boolean) 연산에는 '그리고', '또는', '부정'이 있다.  
종류 | 설명
--- | ---
and | 그리고
or | 또는
not | 부정(반대)

```SCSS
$w: 100px;
.item {
    display: block;
    @if ($w > 50px and $w > 90px) {
        width: 400px;
    }
}

/* compiled to */
.item {
    display: block;
    width: 400px;
}
```

### 재활용 (Mixins)

Sass Mixins은 재사용 할 CSS 선언 그룹을 정의하는 기능이다.
선언하기(@mixin)과 포함하기(@include)로 만들(선언)고, 사용(포함)한다.

```SCSS
// SCSS
@mixin 믹스인이름 {
    스타일;
}

@include 믹스인이름;

// Sass
=믹스인이름
    스타일

+믹스인이름

// 예시
@mixin size ($w: 100px, $h: 100px) {
    width: $w;
    height: $h;
}

.box1 {
    @include size;
}
.box2 {
    @include size($h: 300px);
}
.box3 {
    @include size;
}

/* compiled to */
.box1 {
    width: 100px;
    height: 100px;
}
.box2 {
    width: 100px;
    height: 300px;
}
.box3 {
    width: 100px;
    height: 100px;
}
```

Mixin은 선택자를 포함하고, 상위(부모) 요소 참조(&) 가능하다.

#### 인수(Arguments)

Mixin은 함수처럼 인수를 가질 수 있다.  

- 매개변수(Parameters) : 값이 들어가는 위치
- 인수(Arguments) : 대입되는 값

```SCSS
// SCSS
@mixin 믹스인이름($매개변수) {
    스타일;
}
@include 믹스인이름(인수);

//Sass
=믹스인이름($매개변수)
    스타일

+믹스인이름(인수)

// 예시
@mixin dash-line($width, $color) {
    border: $width dashed $color;
}

.box1 {@include dash-line(1px, red);}
.box2 {@include dash-line(4px, blue);}

/* compiled to */
.box1 {
    border: 1px dashed red;
}
.box2 {
    border: 4px dashed blue;
}
```

##### 인수의 기본값 설정

인수(argument)는 기본값을 가질 수 있다.  
@include 포함 단계에서 별도의 인수가 전달되지 않으면 기본값이 사용된다.

```SCSS
@mixin 믹스인이름($매개변수: 기본값) {
    스타일;
}

@mixin dash-line($width: 1px, $color: black) {
    border: $width dashed $color;
}

.box1 {@include dash-line;}
.box2 {@include dash-line(4px);}

/* compiled to */
.box1 {
    border: 1px dashed black;
}
.box2 {
    border: 4px dashed black;
}
```

##### 키워드 인수

Mixin에 전달할 인수를 입력할 때 명시적으로 키워드명을 입력하여 작성가능하다.  
인수는 기본적으로 순서대로 대입되므로, 앞에 인수를 기본값으로 적용할 때 사용한다.

```SCSS
@mixin 믹스인이름($매개변수A: 기본값, $매개변수B: 기본값) {
    스타일;
}

@include 믹스인이름($매개변수B: 인수);
```

##### 가변 인수

입력할 인수의 개수가 불확실한 경우 가변 인수를 활용한다.  
가변 인수는 매개변수 뒤에 ...을 붙여주며, 마지막 매개변수가 그 값을 다 안는다.

```SCSS
@mixin 믹스인이름($매개변수...){
    스타일;
}

@include 믹스인이름(인수A, 인수B, 인수C);

// 예시
@mixin var ($w, $h, $bg...) {
    width: $w;
    height: $h;
    background: $bg;
}

.box {
    @include var(
        100px,
        200px,
        url("image/a.png") no-repeat 10px 20px,
        url("image/b.png") no-repeat,
        url("image/c.png")
    );
}

/* compiled to */
.box {
    width: 100px;
    height: 200px;
    background: url("image/a.png") no-repeat 10px 20px, url("image/b.png") no-repeat, url("image/c.png")
}
```

##### @content

선언된 Mixin에 @content가 포함되어 있다면 해당 부분에 원하는 스타일 블록을 전달할 수 있다. 이로 인해 기존 Mixin이 가지고 있는 기능에 선택자나 속성을 추가할 수 있다.

```SCSS
@mixin 믹스인이름() {
    스타일;
    @content;
}

@include 믹스인이름() {
    // 스타일 블록
    스타일;
}

// 예시
@mixin icon($url) {
    $::after {
        content: $url;
        @content;
    }
}

.box1 {
    @include icon("image/icon1.png");
}
.box2 {
    @include icon("image/icon2.png") {
        display: block;
        position: absolute;
        width: 100px;
        height: 100px;
    };
}

/* compiled to */
.box1::after {
    content: "image/icon1.png";
}
.box2::after {
    content: "image/icon2.png";
    display: block;
    position: absolute;
    width: 100px;
    height: 100px;
}
```

### 확장(Extend)

특정 선택자가 다른 선택자의 모든 스타일을 가져야 하는 경우 선택자의 확장기능을 통하여 가져올 수 있다.

```SCSS
@extend 선택자;

// 예시
.btn {
    padding: 10px;
    margin: 10px;
    background: blue;
}
.btn-danger {
    @extend .btn;
    background: red;
}

/* compiled to */
.btn .btn-danger {
    padding: 10px;
    margin: 10px;
    background: blue;
}
.btn-danger {
    background: red;
}
```

> 확장은 원치 않는 선택자로 반환될 가능성이 크기에 사용을 권장하지 않는다. Mixin으로 대체하여 사용한다!
