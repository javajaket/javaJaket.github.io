---
layout: page
title: Object & Array 
permalink: "/documentation/object&array/"
---

# 객체
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
function dist(p,q) {
  const dx = q.x - p.x
  const dy = q.y - p.y
  return Math.sqrt(Math.abs(dx)+Math.abs(dy));
}

let p1 = {x:1, y:1}
let p2 = {x:4, y:5}
let d = dist(p1,p2);
```

