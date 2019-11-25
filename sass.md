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
