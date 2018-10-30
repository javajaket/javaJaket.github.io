---
layout: page
title: Object & Array 
permalink: "/documentation/object&array/"
---

# 객체
---

데이터 여러개를 하나로 담을 수 있는 **통(container)**과 같은 **자료구조(data structure)**. 객체에 포함된 **데이터(이름-값 쌍)name-value pair**이 저장되는데, 이를 객체의 **속성(property)**이라고 한다.

```js
const person = {
  name: 'Tom',
  age: 20,
  'languages': ['Korean','English'],
  'favorite number': 7
}
```
`객체리터럴` : {...} 부분이 객체 리터럴,변수에 대입된 객체 안의 프로퍼티 값을 읽거나 쓸 때는 **속성접근자(property accessor)**인 마침표(.)연산자 또는 대괄호([])연산자를 사용

```js
person.name // 'Tom'
person['languages'] // ['Korean','Enlish]
person.address = '서울특별시' // 새속성 추가
'name' in person // true (속성이 객체에 존재하는지 확인)
delete person.age // 삭제
```

<br>
### 원의 넓이
property에 저장된 값의 타입이 함수면 **메서드**라고 부른다.
```js
const circle = {
  center: {x:1.0, y:2.0},
  radius: 2.5,
  area: function() {
    return Math.PI * Math.pow(this.radius,2);
  }
}
console.log(circle.area()); // 19.634954084936208
```
함수 객체 안에 적힌 this는 그 함수를 메서드로 가지고 있는 객체를 가리킨다.this 키워드를 사용하면, 메소드 호출 시에 해당 메소드를 갖고 있는 객체에 접근 할 수 있다.

```js
const person = {
  name: 'Tomas',
  age: 20,
  introduce() {
    return `안녕하세요, 제 이름은 ${this.name}입니다. 제 나이는 ${this.age}살 입니다.`
  },
  getOlder() {
    this.age++
  }
}

person.introduce(); //안녕하세요, 제 이름은 Tomas입니다. 제 나이는 20살 입니다.
person.getOlder();  //undefined
person.introduce(); //안녕하세요, 제 이름은 Tomas입니다. 제 나이는 21살 입니다.

function favorite() {
  return `제가 좋아하는 색깔은 ${this.color}입니다.`;
}

const person1 = {
  color: 'green',
  favorite
}

const person2 = {
  color: 'yellow',
  favorite
}

person1.favorite();
person2.favroite();
```
같은 함수임에도 불하고 어떤 객체의 메소드로 사용되느냐에 따라 메소드 내부의 this가 가리키는 객체가 달라질 수 있다.

<br>
# 함수
---

일련의 처리를 하나로 모아 언제든지 호출할 수 있도록 만들어 둔 것

```js
function add(x,y) {
  let result = x + y
  return result;
}
```
- add라는 **이름**을 갖는 함수를 정의
- 괄호 안의 x와 y를 **매개변수,인자(parameter)**
- return 뒤에 오는 값을 **반환값(return value)**

```js
add(2,3); //5
```
- 괄호 안에 넘겨준 2,3을 **인수(argument)** <br>


### 두 점사이의 거리
```js
let p1 = {x:1, y:1};
let p2 = {x:4, y:5};

function dist(p,q) {
  const dx = q.x - p.x
  const dy = q.y - p.y
  return console.log(Math.sqrt(Math.abs(dx*dx) + Math.abs(dy*dy)));
}

dist(p1,p2);
```
<br>
## 호이스팅(hosting)
자바스크립트 엔진은 변수 선언문과 마찬가지로 프로그램의 첫머리로 끌어올린다.함수를 정의하기 전에 함수를 실행하는 코드를 작성해도 문제 없이 작동
```js
console.log(square(5));
funtion square(x) {return x * x}
```
<br>
## 참조에 의한 호출과 값에 의한 호출
함수는 원시 값을 매개변수로 넘겼을 때와 객체를 매개변수로 넘겼을 때 다르게 동작
```js
function square(x) {return x * x;}
let a = 3;
let b = square(a);
console.log("a = " + a + ", b = " + b);
// a = 3, b = 9
```
- 매개변수에 원시 값을 넘기면 그 값 자체가 인자에 전달 => **값의 전달**
- 변수 a와 변수 x는 다른 영역에 메모리에 위치한 별개의 변수,x값을 바꾸더라도 a값은 바뀌지 않는다.

```js
function add(num) { num.x = num.x + 1; num.y = num.y + 1; return num;}
let a = {x:2,y:4}
let b = add(a);
console.log(a,b);
```
- 매개변수로 객체를 넘겼을 때 전달되는 값은 참조 값 => **참조 전달**
- 이전과 다르게 변수 a에 객체 {x:2, y:4}의 참조가 저장되어 있다. 함수 안에서 수정하는 행위는 a의 참조를 수정하는 행위와 같다.

<br>
## 변수의 유효범위 

변수에 접근할 수 있는 범위를 **유효범위(Scope)**라고 한다.
- 전역변수(Global variable)는 함수 바깥에서 선언된 변수로 유효범위가 전체 프로그램
- 지역변수(Local variable)는 함수안에서 선언된 변수와 함수 인자로 변수가 선언된 함수 내부

```js
const a = "global";
function f() {
  const b = "local"
  console.log(a) // "global"
  return b;
}
f();
console.log(b); // referenceError: b is not defined
```
변수 b의 유효범위는 f함수 내부까지이고 변수 a의 유효범위는 f함수 내부 포함 전체 프로그램이다.

- 어휘적스코핑(Lexical Scoping)는 코드가 작성된 구조에 의해서 결정되는 것

<br>
## 함수 안에서의 변수 선언 생략
```js
function f() {
  a = "local"
  console.log(a); //local
  return a;
}
f();
console.log(a); //local
```
언뜻 보기에 변수 a는 함수 f의 지역변수처럼 보이지만 var로 선언하지 않았으므로 실제로는 전역 변수이다.

<br>
## let,const,var 차이
- let과 const는 같은 이름을 갖는 변수의 재선언을 허용하지 않는다.

```js
let x = 1;
let x = 2; //Duplicate declaration "x"
const x = 3; //Duplicate declaration "x"

function a(y) {
  let y = 1; ////Duplicate declaration "y"
}
```
- var문과는 달리 let문으로 선언한 변수를 끌어올리지 않는다.

```js
console.log(x);  //ReferenceError: x is not defined
let x = 3;
```

- let과 const는 블록 스코프(block scope)를 갖는다.

```js
let x = "out x";
{
  let x = "inner x";
  let y = "inner y";
  console.log(x); // inner x
  console.log(y); // inner y
}

console.log(x);  // out x
console.log(y);  // ReferenceErroe: y is not defined
```
중괄호 바깥에 있는 변수 x의 유효범위는 전체이며, 안에 있는 변수 x,y의 범위는 중괄호 안쪽이다. 변수 y를 중괄호 바깥에서 읽으려고 하면 오류가 발생한다.

const문은 블록 유효 범위를 가지면서 한 번만 할당할 수 있는 변수를 선언
```js
const c = 1;
c = 5; //Uncaught TypeError
```
선언한 상수 값은 수정할 수 없지만, 상수 값이 객체이거나 배열일 경우에는 프로퍼티 또는 프로퍼티 값을 수정할 수 있다.

```js
const number = {x:1, y:2};
number.x = 5;
console.log(number); // Object {x:5, y:2}
```
<br>
`함수리터럴`: function(x) {...}부분이 함수 리터럴이며, 이름이 없는 함수이므로 익명 함수라고 부른다. 

```js
const add = function(x,y) {
  return x + y;
}
add(1,2); //3
//호출을 하려면 변수에 저장한 후에 변수의 이름을 통해 호출해야 한다.
```

익명 함수는 함수를 만든 쪽이 아니라 다른 쪽에서 그 함수를 호출할 때 많이 사용된다. 대표적인 예가 함수를 인수로 넘겨줄 때이다. 

```js
[1,2,3,4,5].filter(function (x) {
  return x % 2 === 0;
}); // [2,4]
//배열의 filter메소드에 필터링할 조건을 표현하는 함수를 넘겨주면, filter 메소드쪽에서 배열 각 요소에 대해 함수를 호출한 뒤, true를 반환한 요소만을 필터링해서 반환
```

