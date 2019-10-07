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
