# Sass

CSS Preprocessor : CSS 전(예비) 처리기

CSS는 상대적으로 low 하며 raw한 문법이다. 프로젝트의 크기가 커질수록 불필요한 반복 작업들이 늘어난다.
하지만 웹에서 동작하는 HTML의 스타일을 입히는 언어는 CSS가 유일하다. 따라서 Sass는 직접적으로 웹에 적용되지 않고 컴파일 단계를 거친다.

전처리라는 것은 CSS로 변환되기 전에 작성되기에 전(예비)처리라고 하며, Less, Sass(SCSS), Stylus가 대표적이다.

## Sass와 SCSS의 차이

- Sass(Syntactically Awesome Style Sheets)의 3버전에서 새롭게 등장한 SCSS는 CSS 구문과 완전히 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능을 지원하는 CSS의 상위집합 (Superset)이다.  
즉, SCSS는 CSS와 거의 같은 문법으로 Sass 기능을 지원한다.
- 쉽고 간단한 차이는 {} (중괄호)와 ;(세미콜론)의 유무 / Mixins(믹스인) 방식의 차이 등이 있다.
