# Mordern Javascript

## 자료형
### 숫자형
- number : 자바스크립트에서는 소수,정수 모두 숫자형 number
- syntactic Sugar : 자주 쓰이는 표현을 간략하게
    - x = x + 1;  => x += 1;
    - x += 1; => x++;

- string : 문자형, 자바스크립트에서는 문자열 덧셈은 작동되지만 곱셈은 작동안됨. repeat 함수 활용

- boolean : 논리형, 구문에 참,거짓 판별
- 표시 기호
    - and = &&
    - or = ||
    - not = !

### 형 변환
- 문자열을 숫자로, 혹은 숫자를 문자로 변환
- Number("7"), String(7) 로 형변환을 한다.
    - javascript에서 타입명은 첫번째 글자 대문자로 작성하여야 한다.
    - window.prompt는 언제나 문자열로 출력하기에 Number()로 결과값을 감쌀때, 활용한다.

### 배열 (array)
- 여러 자료를 저장할 때 사용
- 배열 안에는 여러 형태가 저장 가능하다.=> (한 배열안에 숫자형, 문자형, 논리형 동시 저장 가능)
- 배열은 typeof에서 object로 확인된다.
- 내용을 []로 묶어서 저장하며, 배열명[index]로 불러온다.
- index는 0부터 시작
    - var ipad = [199, 'black', true];
    - ipad[2];

#### 문자열 과 배열
- 문자열은 js에서 배열처럼 알파벳 집합으로 인식
- 공통적으로 적용되는 부분도 있지만 차이점도 존재
- mutable / immutable

```javascript
var text1 = 'hello';
var text2 = ['h','e','l','l','o'];
console.log(text1[2]);
console.log(text2[2]);
console.log(text1.length);
console.log(text2.length);

console.log(typeof text1); /* string */
console.log(typeof text2); /* object */

console.log(text1 == text2); /* false */

// 배열은 mutable
var text1 = ['h','e','l','l','o'];
text1[0] = 'b';
console.log(text1);  /* ['b','e','l','l','o']

// 문자열은 immutable
var text2 = 'hello';
text2[0] = 'b';
console.log(text2);  /* hello */
```

#### 2차 배열 (배열 안에 배열)
- 배열 안에 배열 존재 가능

```javascript
var brands = ['apple', 'coca-cola', 'starbucks'];

var products = [
['iphone', 'imac', 'macbook'],
['coke', 'diet coke'],
['americano', 'latte', 'tea']
];

console.log(products[0][1]); /*. imac. */
```