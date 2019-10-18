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

### 객체(object)

- 배열보다 진화한 단계의 객체
- 객체의 구성 (name / value / property)
- 객체는 선언 시 {} 안에 프로퍼티를 작성한다.
- 각 프로퍼티를 ,(comma)로 구분하며 name : value 의 문법으로 기입한다.
- 값(value)에 문자열은 반드시 ""를 붙인다.
- 객체를 불러올때 []와 . 으로 호출가능하며 [] 호출 시 name에 ""를 붙여 호출

```javascript
 var person = {
        name: "ABC",
        age: 100,
        nationality: "korea"
 };  

 console.log(person["name"]);  /* ABC */
 console.log(person.name);   /* ABC */

 ```

- 객체의 명칭
    - name / age / nationality => name/key
    - "ABC", 100, "KOREA" => value
    - name = "ABC", age = 100, nationality = "KOREA" => property

___

## 함수

- 함수에는 함수명, 인자(파라미터), 수행부분이 존재

```javascript
/* 문법 */
function 함수명(파라미터) {
    수  행  문;
}

function logTask(task){
    console.log(task + ": 완료");
    console.log("-");
}
```

- 함수 작성시 주의사항으로는 형변환 할때 String처럼 대문자 주의
    - String(a) => 첫글자 대문자 / 괄호 안에 기호 없음
- 파라미터가 문자열로 자동 변환되는걸 의식하여 함수안에서 형변환을 명시해줄것!

### return

- 함수의 결과값을 돌려준다.

```javascript
function inchToCentimeter(inch) {
    var centimeter = inch * 2.54;  // 1 inch = 2.54cm
    return centimeter;             // cm로 계산한 결괏값 돌려주기
}

var result1 = inchToCentimeter(2); // 2 inch를 cm로 바꾼 값
var result2 = inchToCentimeter(3); // 3 inch를 cm로 바꾼 값

console.log(result1);   // 5.08
console.log(result2);   // 7.62
console.log(inchToCentimeter(1) + inchToCentimeter(5));   // 15.24
```

- 조금 혼동될 수 있는 부분은 inchToCentimeter 함수 안에 변수 centimeter와 함수 호출 시 변수 result1 부분
    - inchToCentimeter 함수의 결과값을 변수 centimeter에 담고 그것을 변수 result1에 담는다.

### 내장함수

- 자바스크립트에 기본적으로 내장되어 있는 함수

#### 형 변환 함수

형 변환 함수는 첫번째 문자를 대문자로 작성

- String(3);
- Number('7');

#### parseInt 함수

숫자와 문자가 섞여 있을 때, 숫자만 꺼내서 반환  
<span style="color:red">숫자가 앞에 있어야만 제대로 작동</span>

- parseInt('100세');    /*  100세  */
- parseInt('세100');    /*  NAN  */ (Not a Number)

#### 그밖에 내장 함수들

- parseFloat(): 문자열 안에서 숫자 (소수 포함)을 뽑아주는 함수
- alert(): 사용자에게 메시지를 띄워주는 함수
- prompt(): 사용자에게 메시지를 띄우고, 문자열을 입력받는 함수
- confirm(): 사용자에게 메시지를 띄우고, 확인과 취소 중 하나를 누르게 하는 함수

### if문

- if (조건부문){수행부문};
- else if (조건부문){수행부문};
- else {수행부문};

### switch문

- switch (변수명){case : break(continue); default : break;}
- 모든 케이스가 순차적 연결 일때 스위치문이 적합 (break를 생략하여 구현 가능)

## 반복문

### for 반복문

- for (let i = 0; i < 5; i++) {수행부분}
- for문과 if문의 중첩은 활용에 가장 흔한 경우

### for of 반복문 (of for문) //ES6 부터 적용

- for문에 불필요한 i 대신 배열을 불러 올수 있음
- for(매개변수 of 배열이름) {수행부분}
- 결과값으로 value를 출력한다.

```javascript
var brands = ['NIKE','ADIDAS','REEBOK'];

for (brandName of brands) {
console.log(brandName);
}
/* 출력
NIKE
ADIDAS
REEBOK
*/
```

### for in 반복문

- 위에 for in과 비슷한 용도와 문법
- 차이점으로는 결과값으로 배열에 index를 출력한다.

```javascript
var brands = ['NIKE','ADIDAS','REEBOK'];

for (brandName in brands) {
console.log(brandName);
}
/* 출력
0
1
2
*/
```

### while 반복문

- while (조건부문) {수행부문}
- 초기화는 while문 앞에 작성하고, i++는 수행부분에 작성

```javascript
var i = 0;
while (i < 6) {
    console.log(brands[i]);
    i++
}
```

#### break문

- 반복문에서 조건부분과 상관 없이 반복문에서 나오는 기능

#### continue문

- 현재 진행되고 있는 수행 부분을 중단시키고 바로 조건부분으로 돌아가서 다음 수행

### for문 vs while문

- 기능적인 차이는 크게 없다.
- 경우에 따라 적합하고 보기 좋은 차이
- 반복 횟수가 예측 가능할 때는 for문 추천
- 반복 횟수를 예측할 수 없을 때 while문 추천
- javascript flag 참조

[자바스크립트의 자동 형변환](https://velog.io/@jakeseo_me/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%9D%BC%EB%A9%B4-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-33%EA%B0%80%EC%A7%80-%EA%B0%9C%EB%85%90-4-%EC%95%94%EB%AC%B5%EC%A0%81-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98-%EB%B2%88%EC%97%AD)  
-확인하고 위치시킬것!

