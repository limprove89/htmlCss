# JAVA SCRIPT

프론트앤드에서 동적 요소를 담당하는 javaScript

- HTML
- CSS
- Java script

이 세가지는 웹 개발에 있어 가장 필수적인 요소이며, 모든 웹에 기본이 되는 기술이다. 이번 세션에서는 java script를 정리해나가도록 하겠다.

___

## 문법

### Expression

- 표현식
- 값을 만들어내기 때문에 함수의 인자로 사용 가능

### Statement

- 문장
- 숫자 혹은 문자들의 연산
- 마지막에 세미콜론으로 완료한다.

### keywords

- 자바스크립트에서 특정한 목적을 위해 사용되는 단어
- 이러한 키워드들은 예약어로 지정되어 있다.

### Reserved words

- 자바스크립트에서 특정 기능을 담당하기에 프로그램 작성 시 변수명, 함수명 등 이름으로 사용할 수 없는 단어

### Future reserved keywords

- 앞으로 특정한 목적을 위해 사용 가능성이 있어서 사용할 수 없는 예약어

### Reserved keywords

- 이미 특정한 목적을 위해 사용하기 때문에 사용할 수 없는 예약어

### identifier (식별자)

- 코드 내의 변수, 함수, 속성을 식별하는 문자열
- 대소문자를 구분한다
- 숫자를 사용가능 하지만 시작할 수는 없음
- 예약어, 공백 사용 불가

### comments (주석)

- 소스 코드에서 프로그램에 영향을 주지않고, 무시되는 부분
- 자신, 동료 개발자가 소스코드를 이해할 수 있도록 돕는 역활로 사용
- 한줄 주석 //  여러줄 주석 /* */

### variable / constant (변수/상수)

- const 상수이름; (es6 이후 대표적인 상수)
- let 변수이름; (es6 이후 대표적인 변수)
- var 변수이름; (es5 까지 대표적인 변수)
- 상수는 선언하고 값을 바로 대입하여야 하며, 그 값은 변하지 않는다.
- 변수는 값을 바로 선언하지 않아도 되며, 값을 대입하여도 유동적으로 변경 가능하다.
- const -> 재선언 불가, 재할당 불가
- let -> 재선언 불가, 재할당 가능
- var -> 재선언 가능, 재할당 가능
- var가 유연한 것으로 보이지만 많은 오류를 발생시킬 수 있다.

### scope of variables (변수의 유효 범위)

- const, let은 블록 스코프
  - {} 블록 안에서만 그 값이 유효하다.
  - 블록 밖에서 호출을 하면 정의되지 않는다.
- var는 함수 스코프
  - 함수 영역이 유효 범위
  - 함수 영역 안에서 변수 var를 정의하고 함수 밖에서 호출하면 정의되지 않는다.
- var를 블록 스코프에서 호출하는 경우
  - 블록 영역 안에서 var를 정의하고 밖에서 호출한 경우 동작한다.
  - var는 함수 스코프이기에 블록 스코프가 적용되지 않는다.
  - 부자연스러운 동작이므로 블록에서는 let, const를 이용한다.
- 주의할 점은 선언과 할당의 개념 구분

### var hoisting

- 호이스팅은 하단에 선언만을 위로 끌어올려 적용
- var에만 적용되며, let,const는 적용 안됨
- 호이스팅은 할당이 아닌 선언만을 올림

___

### 자료형 (data type)

- 자바스크립트는 동적 타이핑
- 변수를 선언하고 후에 할당을 자유롭게 변경 가능
- 할당 값이 변경될 때마다 변수에 자료형은 변화
- 따라서 js는 변수가 가지는 고정 타입이 없다.  

- 기본 타입 (Primitive values)
  - boolean
  - Null
  - Undefined
  - Number
  - String
  - Symbol (ECMA6에서 추가)
- 객체 (objects)
  - object  

- null의 타입은 objcet, undefined 타입은 undefined
- null과 undefined는 ==로는 일치/===로는 불일치
- template string (ECMA6 추가) `` 사이에 기입
- symbol은 동일한 인자라도 독립적으로 구분
- symbol은 new 생성자가 작동 안됨

___

## 조건문

- 표현식이 참으로 평가될 때, 실행되는 블럭
- 조건문 블럭은 {중괄호}안에 한개 이상에 statement
- 블록에 코드가 한줄이면, 중괄호 {} 생략가능
- 표현식이 참/거짓으로 평가되는 경우
  - 참(truethy): true, 37, 'Mark', {}, []
  - 거짓(falsy): false, 0, '', null, undefined, NAN

### if / else if / else

- 조건을 하나가 아닌 여러 조건 판별
- else 안에 if / else if / else 가 들어갈수도 있음

### 논리 연산자

- and: &&
  - 표현식 && 표현식
  - 둘 다 참 일때 참이다.
  - 앞 표현식이 참일때, 뒤 표현식을 평가할 필요가 생기기에 뒤 표현식이 실행
- or: ||
  - 표현식 || 표현식
  - 둘 중 하나만 참이면 참이다.
  - 앞 평가식이 참이면, 뒤 표현식을 평가할 필요가 없어서 실행되지 않는다.
- not: !
  - 앞 표현식이 거짓일 때만 뒤 표현식 실행

### 삼항 연산자

- 조건 ? :
- 조건 ? 조건이 참이면 실행되는 표현식 : 조건이 거짓이면 실행되는 표현식
- 중괄호 {}를 사용할 수 없는 문법

```javascript
let n = 5;

console.log(n % 5 === 0 ? A : B);
```

### switch

- switch 뒤 괄호안에 값이 무엇인지 중괄호 안에 있는 코드들을 비교해서 실행
- default: 뒤에 문장은 항상 참이기에 실행
- case:로 조건 검사 후 실행
- default가 실행되지 않게 case 안에서 break로 끝낼 수 있음

## 반복문

### for문

- 보통 유한한 횟수만큼 반복할 때 사용

```javascript
for (초기화; 반복 조건; 반복이 된 후 실행되는 코드){
반복이 되는 코드 블럭
}
```

- break; => 반복문 종료
- continue; => 해당 블럭 수행 종료 (실행하지 않고 다음 반복으로 넘어감)

### while문

- 조건이 거짓이 될 때까지 반복 실행

```javascript
while(조건){
조건이 거짓이 될 때까지 반복 실행
}
```

### do while문

- 조건을 실행 한 후 거짓이 될 때까지 반복 실행

### for of문

- iterable 객체에 모두 사용 가능
- 배열에 사용

### for in문

- 모든 프로퍼티 (객체) 사용 가능

___

## 함수

- 자바스크립트에서 함수는 표준 내장 객체
- 함수 선언 방법
  - function 함수명(매개변수){실행부분}  /*  선언적 function  */
  - const hello = function(매개변수){실행부분}    /*  익명함수를 변수에 대입  */
  - const hello = new Function('매개변수','수행부분'); /* 생성자 함수를 변수에 대입  */
  - const hello = (매개변수) => {수행부분};   /* arrow function  */
  - function Person(name, age) {this.name = name; this.age = age;}  
  - const p = new Person('Mark', 37);   /*  생성자 함수를 이용한 객체 생성  */

선언함수|익명함수|변수=생성자함수|화살표함수|생성자함수
:---:|:---:|:---:|:---:|:---:
함수 선언 전 상단에서 호출 가능(호이스팅)|함수 선언 전 상단에서 호출 불가|변수와 수행부분 '문자열' 입력, 글로벌 변수만 취급가능| 항상 익명함수로 사용 가능. 매개변수가 하나일 때, 괄호 생략 가능, return 생략 가능|객체를 만들어 인자로 넣어준 값을 프로퍼티로 생성

## 클래스 (es6 추가)

- 객체를 만들 수 있는 새로운 방법

### 클래스 생성 방법

- 선언적 방식
  - class A {}
- class 표현식을 변수에 할당
  - const B = class {};
- 클래스는 호이스팅이 일어나지 않는다!

### 생성자 (constructor)

- 클래스를 이용하여 객체를 생성할 때 외부 인자를 넣을 수 있음

```javascript
class C {
    constructor(name, age) {
        console.log('constructor', name, age);
        }
    }

console.log(new C('Mark', 37));   /*    constructor Mark 37    */
console.log(new C());   /* undefined undefined  */
```

### 멤버 변수

```javascript
class A {
    constructor(name, age) {
        this.name = name;
        this.age = age;
        }
    }

    console.log(new A('Mark', 37));  /*  A { name: 'Mark', age: 37 }  */

class B {
    name;
    age;
}

    console.log(new B());  /*  B {name: undefined, age: undefined }  */

class C {
    name = 'no name';
    age = 0;

    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}

    console.log(new C('Mark', 37));  /*  C {name: 'Mark', age: 37 }  */
```

### 멤버 함수

- 클래스 안에 함수를 담을 수 있다.

```javascript
class A {
    hello1() {
        console.log('hello1',this);
    }

    hello2 = () => {
        console.log('hello2',this);
    }
}

new A().hello1();  /* hello1 A {hello2: [Function: hello2] }  */
new A().hello2();  /* hello2 A {hello2:  [Function: hello2] }  */

class B {
    name = 'Mark';

    hello() {
        console.log('hello', this.name);
    }
}

new B().hello();  /*  hello Mark  */
```

### get / set

- 변수에 _를 붙이면 통상적으로 내부적으로 사용하는 변수를 의미
- 외부에서의 접근은 get/set을 통해서만 변경

```javascript
class A {
    _name = 'no name';

    get name() {
        return this._name + '@@@';
    }

    set name(value) {
        this._name = value + '!!!';
    }
}

const a = new A();
console.log(a);  /* A {_name:'no name'}   */
a.name = 'Mark';
console.log(a); /*  A {_name:'Mark!!!'}   */
console.log(a.name);    /*  A {_name:'Mark!!!@@@'}   */
console.log(a._name);   /*  A {_name: Mark!!!}  */

// read only

class B {
    _name = 'no name';

    get name() {
        return this._name + '@@@';
    }
}

const b = new B();
console.log(b)  /*  B {_name: 'no name' } */
b.name = 'Mark';
console.log(b)  /*  B {_name: 'no name' } */
```

### static 변수/함수

- 객체가 아닌, 직접적인 클래스의 변수와 함수
- 클래스가 붕어빵 틀이라고 하였을 때, static 변수/함수는 틀이 아닌 클래스 자체에 변수/함수
- 따라서 생성자를 통하여 새로운 객체를 생성하였을 때, undefined
- 클래스 내에 호출 시, this가 아닌 클래스명으로 접근해야한다.

```javascript
class A {
    static age = 37;
    static hello() {
        console.log(A.age);
    }
}

console.log(A, A.age);  /*  [Function: A] {age: 37} 37  */
A.hello();  /*  37  */

class B {
    age = 37;
    static hello() {
        console.log(this.age);
    }
}

console.log(B, B.age);  /*  [Function: B] undefined */
B.hello();  /*  undefined   */
// new B().hello(); /* error    */

class C {
    static name = '이 클래스의 이름은 C가 아니다.';
}

console.log(C); /*  [Function: 이 클래스의 이름은 c가 아니다.]  */
```

### extends (상속)

- 부모의 인스텐스를 그대로 상속 가능

```javascript
class Parent {
    name = 'Lee';

    hello() {
        console.log('hello', this.name);
    }
}

class Child extends Parent {}

const p = new Parent();
const c = new Child();

console.log(p, c);  /*  Parent { name: 'Lee' } child { name: 'Lee' }    */
c.hello();  /*  hello Lee   */
c.name = 'Anna';
c.hello();  /*  hello Anna  */
```

### override

- 클래스의 상속 멤버 변수 및 함수 오버라이딩, 추가
- 상속 받은 값 중 부모에 없어 자식이 추가한 값

```javascript
class Parent {
    name = 'Lee';

    hello() {
        console.log('hello', this.name);
    }
}

class Child extends Parent {
    age = 37;

    hello() {
        console.log('hello', this.name, this.age);
    }
}

const p = new Parent();
const c = new Child();

console.log(p, c)   /*  Parent { name : Lee } Child { name : Lee, Age : 37 }    */
c.hello();  /* hello Lee 37 */
c.name = 'Anna';
c.hello();  /* hello Anna 37    */
```

### super

- 클래스의 상속 생성자 함수 변경
- 클래스에서 함수의 변경 사항에 있어 추가 사항 이전에 super(받은 인자값);를 입력하여 기존 동작을 수행하도록 한다.

```javascript
class Parent {
    name;

    constructor(name) {
    this.name = name;
    }

    hello() {
        console.log('hello', this.name);
    }
}

class Child extends Parent {
    age;

    constructor(name, age) {
        super(name);
        this.age = age;
    }

    hello() {
        console.log('hello', this.name, this.age);
    }
}

const p = new Parent('Mark');
const c = new Child('Mark', 37);

console.log(p, c);  /*  Parent { name : Mark } Child { name : Mark, age : 37 }  */
c.hello();  /*  hello Mark 37   */
```

### static

- 클래스의 상속 static 상속

```javascript
class Parent {
    static age = 37;
}

class Child extends Parent {}

console.log(Parent.age, Child.age); /*  37 37   */
```

### Promise

- ES6 부터 표준 내장 객체로 추가
- 생성자로 객체 생성 가능하며 인자로 executor 함수를 이용
- executor 함수는 resolve, reject를 인자로 갖는다.
- promise는 세가지 상태를 갖는다.
- 프로미스 객체가 생성되는 순간 pending(대기) 상태
- resolve 함수가 실행되면 fulfilled(이행) 상태
  - 이행되는 순간 코드는 then()으로 넘어감
  - resolve 함수에 인자를 넣어 실행하면, then(message)의 callback 함수에 인자로 받을 수 있음
- reject 함수가 실행되면 rejected(거부) 상태
  - 거부되는 순간 코드는 catch()로 넘어감
  - reject 함수에 인자를 넣어 실행하면, catch(reason)의 callback 함수의 인자로 받을 수 있음. (error는 주로 reason이 아닌 error객체를 생성하여 넘긴다.)
- fulfilled되거나 rejected 된 후 최종적으로 실행할 것이 있다면, finally()를 설정하고, 함수를 인자로 넣는다.
- promise all은 전체가 fulfilled 되었을 때, then 실행
- promise race는 가장 빠른 하나가r fulfilled 되었을 때, then 실행

> 추천되는 사용방식은 함수의 실행과 동시에 프로미스 객체를 만들면서 pending이 시작하도록 하기 위해서 프로미스 객체를 생성하면서 리턴하는 함수()를 만들어 함수() 실행과 동시에 then을 설정

```javascript
function p() {
  return new promise(resolve, reject) => {
    /* pedding */
    setTimeout(() => {
      reject(new Error('bad'));
    }, 1000);
  });
}

p()
  .then(message => {
    console.log('1000ms 후에 fulfilled 됩니다.', message);
  })
  .catch(error => {
    console.log('1000ms 후에 rejected 됩니다.', error);
  })  
  .finally(() => {
    console.log('end');
  });
```

___

### async function / await

- es2017에서 표준으로 지정
- resolve - then과 같은 맥락 하지만! asyns function안에 await가 담아지도록 하여 사용
- reject 시에는 try{}catch로 감싸서 처리
