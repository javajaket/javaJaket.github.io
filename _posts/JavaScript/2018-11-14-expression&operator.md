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
이처럼 원시 값을 객체로 변환하는 행위를 가리켜 원시 값을 객체로 `래핑(wrapping)`한다고 한다.


String 객체에는 문자열을 처리하기 위한 다양한 프로퍼티와 메서드가 마련되어 있다.[MDN참고](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)

## String 생성자의 메서드

String생성자 또한 일종의 함수이며 프로퍼티를 갖고 있다. 

|     프로퍼티    |     설명      |     비고    |
|     :------   |     :------- | :------    |
| String.length | 항상 1 |        |
| String.fromCharCode() | 인수로 넘긴 문자 코드 목록으로 문자열을 만들어 반환 | |
| String.fromCodePoint() | 인수로 넘긴 코드 포인트 목록으로 문자열을 만들어 반환 | ES6 |
| String.prototype | String의 프로토타입 객체 | |
| String.raw() | 템플릿 문자열의 원지 문자열 형식을 반환 | ES6 |

```js
String.fromCharCode(0xAE38); // 길
String.fromCharCode(65,66,67); //ABC
// 문자코드(UTF-16 인코딩 값)을 문자열로 변환.쉼표로 구분한 문자 코드 여러 개를 인수로 넘기면 각 문자 코드가 뜻하는 문자를 문자열로 연결

let msg = 'New message"
console.log(msg[2]); //w 
// 문자열을 읽을 때는 charAt메서드 대신 대괄호 연산자를 사용할 수 있다.
```

<br>
# 관계 연산자
----

| 연산자 | 예제 | 뜻 |
| ---- | ---- | ---- |
| == | a == b | a 값과 b 값이 같으면 true, 그 외에는 false |
| != | a != b | a 값과 b 값이 다르면 true, 그 외에는 false | 
| === | a === b | a 와 b의 `값과 타입`이 같으면 true, 그 외에는 false |
| !== | a !== b | a 와 b의 `값과 타입`이 다르면 true, 그외에는 false |

일치(===)연산자는 피연산자를 평가한 후에 타입을 변환하지 않은 상태의 두 값을 엄격하게 비교,동일(==)연산자는 내부적으로 좌우 피연산자의 타입을 변환한 다음에 좌변과 우변이 같은지를 느슨하게 비교

<br>
# 논리 연산자
-----

| 연산자 | 예제 | 뜻 | 예제의 뜻 |
| ---- | ---- | ---- | ---- |
| && | a && b | 논리 곱 | a와 b가 모두 true면 true, 그 외에는 false | 
| :: | a :: b | 논리 합 | a와 b중 하나라고 true면 true, 모두가 false면 false | 
| ! | !a | 부정 | a가 true면 false, false면 true |

## 피연산자의 평가

논리 연산자의 피연산자는 논리 값이 아니어도 된다. 논리값이 아니면 필요에 따라 타입을 변환한다.  

```
0, -0,빈문자열(""),NaN,null,undefinde -> false
0을 제외한 숫자, 빈 문자열을 제외한 문자열, 모든 객체,심벌 -> true
```

논리곱(&&)연산자와 논리합(::)연산자는 단락 평가(short-circuit evalution)를 한다. 단락 평가란 첫 번쨰 피연산자 값이 표현식을 결졍하면 두 번쨰 피연산자을 평가하지 않는 것을 말한다. 또한 논리곱 연산자와 논리합 연산자는 논리값(true,false)대신에 마지막으로 평가한 피연산자 값을 반환한다.

```js
// 논리합
true || true // true
true || false // false
false || true // true 
false || false // false
// 논리곱
true && true // true
true && false // false
false && false // false
false && false // false
```

:: 연산자는 여러 개의 값 후보 중에서 null 또는 undefined가 아닌 값을 선택하고자 할 때 유용하세 사용된다. 

```js
let time = time_interval || animationSettings.time || 33;
// time_interval이 정의되어 있을 대는 time_interval 값을 사용, 정의되지 않았을 때는 animationSettings객체의 time 프로퍼티를 사용,그것또한 정의되어 있지 않았을 때는 정수(33)을 사용
```

<br>

# 조건 연산자
---

```js
let num = (a%2 == 0)? '짝수' : '홀수';
```
이때 우변 값은 a % 2가 0일 때(즉,a가 짝수일 때)는 '짝수'가 되고, 그렇지 않을 때(즉,a가 홀수일 때)는 '홀수'가 된다. 조건 연산자는 삼항 연산자이며 첫 번째 피연산자를 조건식으로 평가한 후에 그결과가 true면 두 번째 피연산즐 값으로 삼고, false면 세 번째 피연산자를 값을 삼는다.

## 쉼표 연산자

이항 연산자로 왼쪽 이연산자를 평가하고 오른쪽 피연산자를 평가한 이후에 마지막으로 오른쪽 끝 피연산자의 값을 반환한다.이를 활용하면 여러 문장을 한 문장으로 표현할 수 있다.

```js
// for문에서 자주 사용
for(let i = 0,i<=10,i++){

}
```

## 명시적 타입 변환

숫자의 타입을 문자열로 바꿀 수 있다.
```js
10 + 'number' // '10number'
10 + '' // '10' 숫자에 빈 문자열을 더해 숫자 타입을 문자열로 바꿀 수 있다.
('0000'+12).slice(-4) // '0012' 앞부분에 0을 넣어 네 자릿수 정수를 표현하는 문자열로 만들 수 있다.
```

Number 객체의 메서드를 활용
```js
let n = 15
n.toString()     //인수를 지정하지 않으면 10진수 문자열로 변환
n.toString(2)    // '1111' 2진수 문자열로 변환
n.toString(16)   // 'f' 16진수 문자열로 변환
(15).toString(16)// 'f' 숫자에서 바로 메서드를 사용하고자 할 때는 소괄호로 묶는다.

let x = 1234.567
x.toString()
x.toString(16)
x.toFixed(0)     // '1235'숫자의 소수점 아래 자릿수를 지정한 문자열로 변환
x.toFixed(2)     // '1234.57'
x.toFixed(4)     // '1234.5670'
x.toExponetial(3) // '1.235e+3' 숫자의 소수점 아래 자릿수를 지정한 문자열로 변환하되 지수를 함께 표시
x.toPrecision(3)  // '1.23e+3' 숫자를 유효 숫자가 지정된 문자열로 변환한다. 단, 유효 숫자가 정수부의 자릿수보다 작을 때는 지수로 표시
x.toPrecision(6)  // '1234.57' 
```

String 함수를 활용<br>
String 생성자 앞에 new 연산자를 붙이면 String객체를 생성하는 함수로 사용할 수 있지만, new 연산자를 붙이지 않으면 일반적인 함수로 활용할 수 있다. 이때 String함수의 반환값은 String객체가 아닌 문자열

```js
String(1234.567) // '1234.567'
String(0x1a)     // '26'  
```

### 문자열을 숫자로 변환

수식 안에서 묵지석으로 변환<br>
```js
let s  = '2';
s - 0 // 2;
+s    // 2;
```

parseInt와 parseFloat 함수를 활용<br>
문자열을 해석해서 숫자로 바꾸는 함수.parseInt함수는 문자열을 정수로 바꾸고 parseFloat 함수는 문자열을 부동소수점으로 바꾼다.

```js
parseInt('3.14')          // 3
parseFloat('3.14')        // 3.14
parseInt('3.14 meters')   // 3    숫자 다음에 등장하는 문자열은 무시
parseFloat('3.14 meters') // 3.14 
parseInt('0xFF')          // 255  문자열 앞부분에 0x가 있으므로 16진수로 해석
parseInt('0.5')           // 0
parseInt('.5')            // NaN 문자열 앞부분에 '.'이 있으므로 해석하지 않음   
parseInt('abc')           // NaN 숫자로 해석할 수 없음
```

Number 함수를 활용하는 방법 <br>
Number 생성자 앞에 new 연산자를 붙이면 Number객체를 생성하는 함수로 사용할 수 있지만, new 연산자를 붙이지 않으면 일반 함수로 활용할 수 있다.이때 Number함수의 반환값은 Number객체가 아닌 숫자이다.

```js
Number('2.12314')   // 2.12314
Number(123)         // 123
Number(true)        // 1      모든 데이터 타입을 숫자 타입으로 바꾸는 기능이 있다.
Number(false)       // 0
Number(NaN)         // NaN
Number(undefined)   // NaN
```