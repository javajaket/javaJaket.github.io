---
layout: post
title: expression & operator
category: JavaScript
excerpt: 표현식 및 연산자
tags:
  - JavaScript 
  - expression
  - operator
---


## Table of Contents
 - [표현식 and 연산자](#표현식-and-연산자)
 - [Math객체](#math-객체)
 - [부동소수점&정확도](#부동소수점-및-정확도)


---

# 표현식 and 연산자
---
표현식이란 `결과적으로 어떤 값으로 평가(evaluation)되는 것`.변수, 프로퍼티, 배열 요소, 함수 호출, 메서드 호출도 표현식이다. 이를 연산자를 사용하면 표현식을 조합하여 더욱 복잡한 표현식을 만들어 낼 수 있다.

```js
2 + 3 // 2와 3을 피연산자라고 부른다.(operand)
```
## 연산자 우선순위

한 구문에 여러 개의 연산자를 이어서 쓴 경우, 어떤 연산자는 먼저 계산되고 어떤 연산자는 나중에 계산된다. [MDN참조](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/%EC%97%B0%EC%82%B0%EC%9E%90_%EC%9A%B0%EC%84%A0%EC%88%9C%EC%9C%84)

## 산술 연산자

- 정수끼리 나누어도 결과가 부동소수점이 된다.
- 나머지 연산자 %의 피연산자는 부동소수점이 될 수 있다.
- + 연산자는 피연산자 중 하나가 문자열이면 나머지 피연산자를 문자열로 만든다.
- 계산할 수 없는 경우에는 NaN으로 평가, 산술 연산자의 피연산자가 true면 1, false와 null이면 0으로 평가, undefined이면 NaN으로 평가

```js
0/0 // NaN
"number" * 1 // NaN 
true + true // 2
1 + null // 1
1 + undefined // NaN
```

## 증가 감소 연산자

```js
let a = 1;
++a // a에 1을 더한 다음에 a값을 평가
a++ // a를 평가한 다음에 a에 1을 더한다.
--a // a에 1을 뺀 다음에 a값을 평가
a-- // a를 평가한 다음에 adp 1을 뺀다.
```

```js
a = 1;
b = ++a; // a에 1을 더하고 a를 b에 대입한다.(b는 2,a는 2)
c = a++ + 2; //a + 2를 c에 대입하고 a에 1을 더한다.(c는 4,a는 3)
```

# Math 객체
---

JavaScript에 내장된 Math 객체에는 수 연산을 위한 메서드와 프로퍼티가 있다. [MDN참고](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math)

# 부동소수점 및 정확도
---
산술 연산을 할 때는 숫자에 유효한 자릿수가 있으므로 계산할 때 오차가 발생한다는 점을 염두하기  

자바스크립트의 숫자는 IEEE754로 규정된 64비트 부동소수점이며, 64자릿수의 2진수 부동소수점을 표현

1.ddd..d  부분중 ddd..d가 52비트를 차지한다. 즉 2진수 53자리이므로 2^53 = 10^15.95로 약 16자리가 된다.숫자를 자릿수가 정해진 부동소수점으로 표현하여 계산하면 오차가 발생하는데 이것을 `정확도 문제`라고 한다.

```js
let a = Math.sqrt(100001);
let b = Math.sqrt(100000);

console.log(a,b); //316.2293471517152 316.22776601683796
//일반적으로 값이 가까운 두 수를 뺄셈할 때 정확도 문제가 발생한다. 이것을 정밀도 손실이라고 한다.
console.log(a-b); //0.001581134877255863
//정확한 계산한 값은 다음과 같다. 
console.log(1/(a+b)); //0.0015811348772568783
```

# 문자열
---
```js
'Hello' + 'World!' // 'Hello World!
'1' + '2' // '12'
1 + 'number' // 1 number
true + (new Date()) // trueWed Nov 14 2018 10:02:56 GMT+0900 (KST)
```
- '+'연산자는 피연산자가 모두 문자열이면 문자열로 연결한다.
- 피연산자 중 하나가 문자열 또는 문자열로 변환할 수 있는 객체라면 다른 피연산자의 타입을 문자열로 바꾼 다음 연결

## 문자열 메서드

문자열을 String 객체로 변환하려면 String생성자를 사용한다.
```js 
let msgObj = new String('Hi nice to meet you');
```
이처럼 원시 값을 객체로 변환하는 행위를 가리켜 원시 값을 객체로 래핑(wrapping)한다고 한다.

String 객체에는 문자열을 처리하기 위한 다양한 프로퍼티와 메서드가 마련되어 있다.[MDN참고](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)

