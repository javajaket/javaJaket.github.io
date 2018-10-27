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
{...} 부분이 객체 리터럴,변수에 대입된 객체 안의 프로퍼티 값을 읽거나 쓸 때는 **속성접근자(property accessor)**인 마침표(.)연산자 또는 대괄호([])연산자를 사용

```js
person.name // 'Tom'
person['languages'] // ['Korean','Enlish]
person.address = '서울특별시' // 새속성 추가
'name' in person // true (속성이 객체에 존재하는지 확인)
delete person.age // 삭제
```
property에 저장된 값의 타입이 함수면 **메서드**라고 부른다.
<br><br>
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


