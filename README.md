# HTML/CSS

프론트앤드에 가장 기본적인 부분이라 할 수 있는 
- HTML
- CSS
- Java script

이 세가지는 웹 개발에 있어 가장 필수적인 요소이며, 모든 웹에 기본이 되는 기술이다. 이번 세션에서는 HTML과 CSS를 같이 정리해나가도록 하겠다.

> HTML은 semantic한 작성이 매우 중요하다. 
___
###  블록 요소와 인라인 요소

블록 요소의 특징은
 - div,h1,
 - 사용 가능한 최대 가로 너비를 사용한다.
 - 크기를 지정할 수 있다.
 - width: 100% height: 0으로 시작한다.
 - 수직으로 쌓인다
 - margin,padding 위,아래,좌,우 사용 가능하다.
 - 레이아웃 설정에 최적화


인라인 요소의 특징은
 - spanm img
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

만약 모든 클래스를 div로만 표현한다면, 외적인 부분에는 차이가 없을 수 있지만 웹이 추구하는 시멘틱한 html 구성은 아니다. 이 부분은 html에서 정말 중요한데 모든 부분에 기능적인 설명을 tag로 설명하는것이 브라우저가 웹을 이해하는데 매우 중요한 요소로 작용한다.
