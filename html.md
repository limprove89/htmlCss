# HTML

프론트앤드에 가장 기본적인 부분이라 할 수 있는 
- HTML
- CSS
- Java script

이 세가지는 웹 개발에 있어 가장 필수적인 요소이며, 모든 웹에 기본이 되는 기술이다. 이번 세션에서는 HTML과 CSS를 같이 정리해나가도록 하겠다.

> HTML은 semantic한 작성이 매우 중요하다. 
___
###  블록 요소와 인라인 요소

블록 요소의 특징은
 - div, h1
 - 사용 가능한 최대 가로 너비를 사용한다.
 - 크기를 지정할 수 있다.
 - width: 100% height: 0으로 시작한다.
 - 수직으로 쌓인다
 - margin,padding 위,아래,좌,우 사용 가능하다.
 - 레이아웃 설정에 최적화


인라인 요소의 특징은
 - span, img
 - 필요한 만큼 너비를 사용한다.
 - 크기를 지정할 수 없다.
 - width:0 height:0 으로 시작
 - 수평으로 쌓임
 - margin,padding 위,아래는 사용할 수 없다.
 - text,img 등 컨텐츠 표현에 최적화
 ___
 ### HEAD 영역
 HTML은 기본적으로 이런 구조로 구성되어 있다.

 ```html
<!DOCTYPE html>
<html lang="ko">
<head>
<==== 헤 드 영 역 ====>
</head>
<body>
<==== 바 디 영 역 ====>
</body>
</html>
```

메타데이터란 헤드 영역에 기입되는 컨텐츠의 정보에 관련된 속성정보를 말한다. 헤드 영역에는 css를 연결하는 link태그와 java script를 연결하는 script태그, 그외에 타이틀등 정보를 기입하는 태그들이 존재한다.

>추후에 og:title / twitter:card 등의 태그는 리뷰 예정.

___
### BODY 영역
HTML에 BODY영역을 살펴보면

```html
<<!DOCTYPE html>
<html lang="ko">
<head>
</head>
<body>
    <header> </header>
    <footer> </footer>
</body>
</html>>
```

만약 모든 클래스를 div로만 표현한다면, 외적인 부분에는 차이가 없을 수 있지만 웹이 추구하는 시멘틱한 html 구성은 아니다. 이 부분은 html에서 정말 중요한데 모든 부분에 기능적인 설명을 tag로 설정하는것이 브라우저가 웹을 이해하는데 매우 중요한 요소로 작용한다.

#### H1 ~ H6
제목을 표현하는 엘리먼트로 지켜줘야 할 규약은
- 제목 폰트의 크기를 줄이기 위해 낮은 단계를 사용하지 말것 (폰트사이즈 초기화)
- 제목 단계를 건너뛰지 말것
- h1은 한 페이지에 한번만 사용할 것

#### MAIN
- 한문서에 하나의 요소만 사용

#### ARTICLE
- 독립적으로 구분되거나 재사용 가능한 영역을 설정한다.

#### SECTION
- 문서의 일반적인 영역 설정

#### ASIDE
- 문서의 별도 컨텐츠를 설정한다. (보통 광고나 기타 링크 등의 사이드바)

#### NAV
- 다른 페이지에 링크를 제공하는 영역 설정 (보통 상단 네이게이션바, 카테고리 설정)

#### ADDRESS
- body, article, footer 등에서 연락처 정보 등을 제공하기 위해 사용

#### div
- 주로 본질적인 의미를 가지지는 않으며 꾸미는 목적으로 사용

___
### 문자 컨텐츠

#### \<ol>, \<ul>, \<li>
- 각 항목 \<li>의 정렬된 목록 \<ol>이나 정렬되지 않는 목록 \<ul>을 설정
    - \<ol>과 \<ul>은 자식으로 \<li>만 포함 가능
    - \<li>는 단독으로 사용할 수 없으며, \<ol> 혹은 \<ul>에 자식으로 포함되어야 함
    - 정렬된 목록 \<ol>의 순서는 중요도를 의미하기도 함

#### \<dl>, \<dt>, \<dd>
- \<dl>은 용어의 정의를 위한 대괄호로 사용하며, \<dt>는 key, \<dd>는 value를 의미한다.
- \<dl>은 \<dt>와 \<dd>만을 포함해야 한다.

```HTML
<dl>
    <dt>coffee</dt>
    <dd>coffee is ......</dd>
    <dt>milk</dt>
    <dd>milk is ......</dd>
</dl>
```

#### \<p>
- 하나의 문단을 설정
- 대부분의 내용을 정의할 떄 사용한다.

#### \<hr />
- 문단의 분리를 위한 설정
- 중요한 것은 수평선 표시를 위해 사용하지 말것! 의미적 관점으로만 사용할 것!!

#### \<pre>
- 서식이 미리 지정된 텍스트를 설정.
- 텍스트의 공백과 줄바꿈을 그대로 표시하기 떄문에 모든 들여쓰기를 제거하고 본문 내 붙여쓰기를 할 것!
- 기본적으로 monospace 글꼴 계열로 표시

#### \<blockquote>
- 일반적인 인용문을 설정할 때 사용
___
### 인라인 텍스트 (display : inline)

#### \<a>
- 다른 페이지, 같은 페이지 위치, 이메일 주소, 전화번호 등 다른 URL로 연결하는 하이퍼링크를 설정
- a 태그는 href의 주된 역활로 이루어지는데, 속성에 target, download 등을 이용할 수 있다. 설정 시 href는 그대로 기입한다!
- 현재 페이지 상에서 이동을 진행할 수 도 있다.

#### \<abbr>
- title 속성(전역속성) 을 통하여 약어를 지정.
- onmouseover 시 타이틀에 기입한 약어 설명이 노출된다.

#### \<b>
- 문체가 다른 글자의 범위를 설정
- 특별한 의미를 지니지 않으므로 다른 태그가 적합하지 않을 때 사용
- 글씨가 두껍게 표기

#### \<mark>
- 사용자의 관심을 끌기 위해 하이라이팅 할때 사용 (형광펜을 칠한 듯한 효과)
- 기본 설정은 노란색

#### \<em>
- 단순한 의미 강조를 표시
- 중첩이 가능하며, 중첩될수록 의미가 강조됩
- 이탤릭체로 표시됨

#### \<strong>
- 의미의 중요성을 나타내기 위해 사용
- \<b>과 같은 bold채로 표기되지만 의미있는 형식

#### \<i>
- \<b>와 같이 모든 태그의 적합성을 찾을 수 없는 경우 마지막에 사용
- 다만 텍스트가 아닌 특수 아이콘을 사용하기 위한 태그
- fontawesome처럼 외부 라이브러리 이용 시 \<head>에 \<link>에 위치는 내부 css보다 위에 오도록 한다. (내부적으로 스타일 적용이 차후에 적용될 수 있도록)

#### \<dfn>
- 용어를 정의할 때 사용하는 태그

#### \<cite>
- 책, 논문, 영화등의 창작물의 대한 참조를 설정한다.
- 이탤릭체로 표기 됨

#### \<q>
- 짧은 인용문을 설정한다. inline 속성
- 긴 인용문에는 \<blockquote>를 사용한다. block 속성

#### \<u>
- 밑줄이 있는 글자를 설정
- 의미는 없으며 순수하게 꾸미는 용도이다.
- \<a>와의 혼동이 있기에 주의해서 사용하여야 한다.

#### \<code>
- 컴퓨터 코드의 범위를 설정한다.
- monospace로 표기된다.

#### \<kbd>
- 텍스트 입력 장치(키보드)에서 사용자의 입력을 나타내는 텍스트 범위를 설정

#### \<sup>, \<sub>
- 위 첨자와 아래첨사를 나타낸다.

#### \<time>
- 날짜나 시간을 나타내기 위한 목적으로 사용한다.
- 속성에 datetime으로 YYYY-MM-DD 기입을 해주어야 한다.

#### \<span>
- 본질적으로 아무것도 나타내지 않는 컨텐츠의 영역을 설정한다.

#### \<br>
- 줄바꿈을 설정한다.
- 2개 이상의 사용을 금지한다! 여백 추가는 br이 아닌 css로 요소 padding값을 변경하는것으로 적용하는 것을 권장한다.

#### \<del>, \<ins>
- 삭제된 텍스트의 범위를 지정 / 새로 추가된 텍스크의 범위를 지정
- 중간선으로 삭제를 표시하며, 밑줄로 추가를 표시한다.
___

### 멀티미디어

#### \<img>
- 이미지를 삽입하는 엘리먼트
- width와 sizes 사용 시 width가 적용됨

속성 | 의미 | 값 
--- | --- | ---
src | 이미지 URL | URL
width | 이미지의 가로너비 |
height | 이미지의 세로너비 | 
srcset | 브라우저에게 제시할 이미지 URL과 원본 크기의 목록 정의 | w, x
sizes | 미디어 조건과 해당 조건일 떄 이미지 최적화 크기의 목록 정의 | 

#### \<audio>, \<video>
- 소리(mp3), 동영상(mp4) 등의 컨텐츠를 삽입
- 두 엘리먼트는 속성이 비슷함.
- autoplay가 지정된 경우, preload는 무시됨.
- 코드 작성 시 controls 누락 시 화면 상 표시가 안됨.

속성 | 의미 | 값 | 기본값
--- | --- | --- | ---
autoplay | 준비되면 바로 재생 | boolean | 
controls | 제어 메뉴를 표시 | boolean | 
loop | 재생이 끝나면 다시 처음부터 재생 | boolean | 
preload | 페이지가 로드될 때 파일을 로드할지 지정 | none,metadata,auto | metadata
src | 컨텐츠 URL | URL | 
muted | 음소거 여부 | boolean | 

#### \<figure>, \<figcaption>
- \<figure>는 이미지나 삽화, 도표 등의 영역 설정
- \<figcaption>은 \<figure>에 포함되어 이미지나 삽화 등의 설명을 표시.

```HTML
<figure>
    <img src="milk.jpg" alt="milk">
    <figcaption>milk is very ...</figcaption>
</figure>
```

___
### 내장 컨텐츠

#### \<iframe>
 - 다른 HTML 페이지를 현재 페이지에 삽입. (중첩된 브라우저 컨텍스트(프레임)를 표시)
 - 단순히 동영상을 불러오는 엘리먼트는 아님.

속성 | 의미 | 값 | 기본값
--- | --- | --- | ---
name | 프레임의 이름 | | 
src | 포함할 문서의 URL | URL | 
width | 프레임의 가로 너비 | | 
height | 프레임의 세로 너비 | | 
allowfullscreen | 전체 화면 모드 사용 여부 | boolean | 
frameborder | 프레임 테두리 사용 여부 | 0, 1 | 1
sandbox | 보안을 위한 읽기 전용으로 삽입 | boolean or allow-form, allow-scripts, allow-some-origin | 

#### \<canvas>
- Canvas API, WebGL API를 사용하여 그래픽이나 애니메이션을 랜더링.

속성 | 의미 
--- | ---
width | 캔버스의 가로 너비
height | 캔버스의 세로 너비

___
### 스크립트
#### \<script>

- 스크립트 코드를 문서에 포함하거나 참조 (외부 스크립트)

속성 | 의미 | 값 | 특징 
--- | --- | --- | ---
async | 스크립트의 비동기적 실행 여부 | boolean | src 속성 필수
defer | 문서 파싱 후 작동 여부 | boolean | src 속성 필수
src | 참조할 외부 스크립트 URL | URL | 포함된 스크립트 코드는 무시됨
type | MINE 타입 | text/javascript(기본값) | 통상적으로 생략됨

#### \<noscript>
- 스크립트를 지원하지 않는 경우에 삽입할 HTML을 정의
- 환경상 스크립트의 로드가 되지 않을 경우 내용을 알려주는 용도

___
### 표 컨텐츠

- 전체적인 예시 참조 

```HTML
<table>
  <caption>Fruits</caption>
  <colgroup>
    <col span="2" style="background-color: yellowgreen;">
    <col style="background-color: tomato;">
  </colgroup>
  <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>F123A</td>
      <td>Apple</td>
      <td>$22</td>
    </tr>
    <tr>
      <td>F098B</td>
      <td>Banana</td>
      <td>$19</td>
    </tr>
  </tbody>
</table>
```

#### \<table>, \<tr>, \<th>, \<td>
- 데이터 표 (\<table>)의 행(줄 / \<tr>)과 열( 칸,셀 / \<th>, \<td> )을 생성
- (Table row, Table header, Table data)

#### \<th>
- 머리글 칸을 지정

속성 | 의미 | 값 | 기본값 
--- | --- | --- | ---
abbr | 열에 대한 간단한 설명 | | 
headers | 관련된 하나 이상의 다른 머리글 칸 id 속성 값 | | 
colspan | 확장(병합)하려는 열의 수 | | 1 
rowspan | 확장(병합)히려는 행의 수 | | 1 
scope | 자신이 누구의 '머리글 칸' 인지 명시 | col, colgroup, row, rowgroup,auto | auto

#### \<td>
- 일반 칸을 지정 

속성 | 의미 | 값 | 기본값 
--- | --- | --- | ---
headers | 관련된 하나 이상의 다른 머리글 칸 id 속성 값 | | 
colspan | 확장(병합)하려는 열의 수 | | 1 
rowspan | 확장(병합)히려는 행의 수 | | 1 

#### \<caption>
- 표의 제목을 설정
    - 열리는 TABLE 태그 바로 다음에 작성해야 함 (작성 후 바로 닫기)
    - \<table> 당 하나의 \<caption>만 사용 가능.

#### \<colgroup>, \<col>
- 표의 열들을 공통적으로 정의하는 칼럼과 그의 집합

속성 | 의미 | 값 | 기본값 
--- | --- | --- | ---
span | 연속되는 열 수 | 숫자 | 1

#### \<thead>, \<tbody>, \<tfoot>
- 표의 머리글, 본문, 바닥글을 지정한다
    - 기본적으로 테이블의 레이아웃에 영향을 주지 않음
___    
### 양식

#### \<form>
- 웹 서버에 정보를 제출하기 위한 양식 범위를 정의
  - \<form>이 다른 <form>을 자식 요소로 포함할 수 없음
  
  속성 | 의미 | 값 | 기본값
  --- | --- | --- | ---
  action | 전송한 정보를 처리할 웹 페이지 URL | URL | 
  autocomplete | 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부 | on, off | on
  method | 서버로 전송할 HTTP 방식 | GET, POST | GET
  name | 고유한 양식의 이름 | | 
  novalidate | 서버로 전송시 양식 데이터의 유효성을 검사하지 않도록 지정 | |
  target | 서버로 전송 후 응답받을 방식을 지정 | _self, _blank | _self
  
#### \<input>
- 사용자에게 입력 받을 데이터 양식
  
  속성 | 의미 | 값 | 기본값 | 특징
  --- | --- | --- | --- | ---
  autocomplete | 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부 | on, off | on | 
  autofocus | 페이지가 로드될 때 자동으로 포커스 | boolean | | 문서 내 고유해야 함
  checked | 양식이 선택되었음을 표시 | boolean | | type 속성 값이 radio, checkbox 일 경우만
  disabled | 양식을 비활성화 | boolean | | 
  form | form의 id 속성 값 | | 해당 form의 후손이 아닐 경우만
  
  
- 이외의 많은 속성들이 존재한다. 

---

### 데이터 종류의 값
- type 속성에 입력할 수 있는 값의 목록
  - \<input> 속성에 입력할 수 있는 값의 목록
  
  값 | 데이터 종류 | 특징
  --- | --- | ---
  button | 일반 버튼 | \<button>으로 사용
  checkbox | 체크 박스 | 
  color | 색상 | IE 지원 불가
  email | 이메일 | 
  file | 파일 | 
  number | 숫자 | 
  password | 비밀번호 | 가려지는 양식
  radio | 라디오 버튼 | 같은 name 속성 그룹 내 하나만 선택 가능
  tel | 전화 번호 | 
  submit | 제출 버튼 | 해당 \<form> 범위 내 고유한 양식
  
#### \<label>
- 라벨 가능 요소 (lavelable)의 제목(caption)
  - for 속성으로 라벨 가능 요소를 참조하거나 포함
  - 라벨 가능 요소 : \<botton>,\<input>, \<progress>, \<select>, \<textarea>
  
속성 | 의미
--- | ---
for | 참조할 라벨 가능 요소의 id 속성 값

#### \<botton>
- 선택 가능한 버튼을 지정

속성 | 의미 | 값 | 특징
--- | --- | --- | ---
autofocus | 페이지가 로드될 때 자동으로 포커스 | boolean | 문서 내 고유해야 함
disabled | 버튼을 비활성화 | boolean | 
form | \<form>의 id 속성 값 | | 해당 \<form>의 후손이 아닐 경우만
name | 폼 데이터와 함께 전송되는 버튼의 이름 | | 
type | 버튼의 타입 | button, reset, submit

#### \<textarea>
- 여러 줄의 일반 텍스트 양식

속성 | 의미 | 값 | 기본값 | 특징
--- | --- | --- | --- | ---
autocomplete | 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부 | on, off | on | 
autofocus | 페이지가 로드될 때 자동으로 포커스 | boolean | | 문서 내 고유해야 함
disabled | 양식을 비활성화 | boolean | | 
form | \<form>의 id 속성 값 | | 해당 \<form>의 후손이 아닐 경우만
maxlength | 입력 가능한 최대 문자 수

#### \<fieldset>, \<legend>
- 같은 목적의 양식을 그룹화(fieldset) 하여 제목(legend)을 지정

```HTML
<form>
  <fieldset>
    <legend>Coffee Size</legend>
    <label>
        <input type="radio" name="size" value="tall" />
        Tall
    </label>
    <label>
        <input type="radio" name="size" value="grande" />
        Grande
    </label>
    <label>
        <input type="radio" name="size" value="venti" />
        Venti
    </label>
  </fieldset>
</form>
```
\<fieldset>
- 같은 목적의 양식을 그룹화

속성 | 의미 | 값
--- | --- | 
disabled | 그룹 내 모든 양식 요소를 비활성화 | boolean
form | 그룹이 속할 하나 이상의 form 의 id 속성 값 | 
name | 그룸의 이름 | 

#### \<select>, \<datalist>, \<optgroup>, \<option>
- 옵션 (\<option>, \<optgroup>)의 선택 메뉴 (\<select>)나 자동완성 (\<datalist>)을 제공

```HTML
<select>
  <optgroup label="Coffee">
    <option>Americano</option>
    <option>Caffe Mocha</option>
    <option label="Cappuccino" value="Cappuccino"></option>
  </optgroup>
  <optgroup label="Latte" disabled>
    <option>Caffe Latte</option>
    <option>Vanilla Latte</option>
  </optgroup>
  <optgroup label="Smoothie">
    <option>Plain</option>
    <option>Strawberry</option>
    <option>Banana</option>
    <option>Mango</option>
  </optgroup>
</select>
```

#### \<select>
- 옵션을 선택하는 메뉴

속성 | 의미 | 값 | 기본값
--- | --- | --- | ---
autocomplete | 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부 | on, off | on
disabled | 선택 메뉴를 비활성화 | boolean | 
form | 선택 메뉴가 속할 하나 이상의 \<form>의 id 속성 값 | | 
multiple | 다중 선택 여부 | boolean | 
name | 선택 메뉴의 이름 | | 
size | 한 번에 볼 수 있는 행의 개수 | number | 0 (1과 같음)

#### \<datalist>
- \<input>에 미리 정의된 옵션을 지정하여 자동완성 기능을 제공하는 데 사용
  - \<input>의 list 속성 바인딩
  - \<option>을 포함하여 정의된 옵션을 지정

```HTML
<input type="text" list="fruits">

<datalist id="fruits">
  <option>Apple</option>
  <option>Orange</option>
  <option>Banana</option>
  <option>Mango</option>
  <option>Fineapple</option>
</datalist>
```

#### \<optgroup>
- \<option>을 그룹화

속성 | 의미 | 값
--- | --- | ---
label | (필수)옵션 그룹의 이름 | 
disabled | 옵션 그룹을 비활성화 | boolean

#### \<option>
- 선택 메뉴 (\<select>)나 자동완성(\<datalist>)에서 사용될 욥션
  - 선택적 빈 태그로 사용

속성 | 의미 | 값 | 특성
--- | --- | --- | ---
disabled | 옵션을 비활성화 | boolean | 
label | 표시될 옵션의 제목 | | 생략되면 포함된 텍스트를 표시
selected | 옵션이 선택되었음을 표시 | boolean | 
value | 양식으로 제출될 값 | | 생략되면 포함된 텍스트를 값으로 사용

#### \<progress>
- 작업의 완료 진행률을 표시

속성 | 의미 | 값 | 특징
--- | --- | --- | ---
max | 작업의 총량 | number | 
value | 작업의 진행량 | number | max 속성을 생략할 경우 0~1 사이의 숫자여야 함

### 전역 속성 (global Attributes)
- 모든 HTML 요소에서 공통적으로 사용 가능한 속성.

#### class
- 공백으로 구분된 요소의 별칭을 지정
- CSS 혹은 JavaScript의 요소 선택기를 통해서 요소를 선택하거나 접근한다.

#### id
- 문서에서 고유한 식별자를 정의
- CSS 혹은 JavaScript의 요소 선택기를 통해서 요소를 선택하거나 접근한다.

#### style
- 요소에 적용할 CSS를 선언

#### title
- 요소의 정보(설명)을 지정

#### lang
- 요소의 언어를 지정

#### data-*
- 사용자 정의 데이터 속성을 지정
- HTML에 JavaScript에서 이용할 수 있는 데이터를 저장하는 용도로 사용.
- HTML에서는 -문법을 선호, JavaScript에서는 Camel표기법을 선호

```HTML
<!-- data-custom-data-attributes -->
<div id="me" data-my-name="Heropy" data-my-age="851">Heropy</div>
```

```javascript
// dataset.customDataAttributes
const $me = document.getElementById('me');
console.log($me.dataset.myName); // "Heropy"
console.log($me.dataset.myAge); // "851"
```

#### draggable
- 요소가 Drag and Drop API를 사용 가능한지 여부를 지정.
- 생략 하였을 경우에는 true나 false가 아닌 auto로 설정된다.

#### hidden
- 요소를 숨김

```html
<form id="hidden-form" action="/form-action" hidden>
  <!-- 숨겨진 양식들.. -->
</form>
<button form="hidden-form" type="submit">전송</button>
```

#### tabindex
- Tab 키를 이용해 요소를 순차적으로 포커스 탐색할 순서를 지정
  - 대화형 컨텐츠는 기본적으로 코드 순서대로 탭 순서가 지정됨
  - 비대화형 컨텐츠에 tabindex="0"을 지정하여 대화형 컨텐츠와 같이 탭 순서를 사용
  - tabindex="-1"을 통해 포커스는 가능하지만 탭 순서에서 제외 가능
  - tabindex="1" 이상의 양수 값은 논리적 흐름을 방해하기 때문에 사용을 추천하지 않음!

___

### 절대 경로와 상대 경로

#### 절대경로
- / 이전 https://xxx.xx.com 까지 생략 가능 

#### 상대경로
- ./  -> 현재 경로
- ../ -> 이전 경로

___
### 그 외 필요한 문법

#### 주석
- 개발자가 개발 과정에서 코드에 관한 설명을 부여할 때 사용.
- 협업 및 개발자 본인이 훗날 코드 리뷰 시 이해가 쉽도록 기입하여야 한다.
- 거의 모든 에디터에서는 언어에 관계없이 'cmd' + '/' 으로 단축키 설정 되어 있다.

#### 엔티티
- HTML에서 특수기호가 화면 상 출력이 될 수 있는 기호의 코드화
- &nbps;(공백) &lt;(왼쪽꺽쇠) %gt;(오른쪽꺽쇠) 등이 있다.

