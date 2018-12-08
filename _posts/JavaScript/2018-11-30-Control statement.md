---
layout: post
title: Control statement
category: JavaScript
excerpt: 제어 구문
tags: 
  - JavaScript
  - Conditional statement
  - Looping statement
---

# 조건문 
조건식의 값에 따라 실행 흐름을 분기한다.

## if/else문
조건에 따라 특정 영역의 코드를 실행시키거나 실행시키지 않을 수 있다.
```js
if(num == 1) {
  console.log('one')
} else if(num == 2) {
  console.log('two')
} else {
  console.log('Other')
}
```
```js
// 고혈압 여부 확인하기
if(hp<120 && lp<80) {
  judgement.innerHTML = '정상';
} else if(139>hp && 89>lp) {
  judgement.innerHTML = '불안';
} else {
  judgement.innerHTML = '비정상';
}
```

## switch
switch문을 사용하면 분기점 여러 개를 간결하게 표현할 수 있다.

```js
function translateColor(english) {
  let result;
  switch(english) {
    case 'red':
      result = '빨강색';
      break;
    case 'blue':
      result = '파랑색';
      break;
    case 'purple':
      result = '보라색';
      break;
    case 'violet':
      result = '보라색';
      break;
    default:
      result = '일치하는 색깔이 없습니다.'
  }
  return result;
}
```
switch 문이 실행되면 먼저 괄호 안에 들어 있는 표현식을 평가하고 평가한 값과 일치하는 case 라벨의 값을 위에서부터 아래 방향으로 찾는다. break 문이 실행되면 블록 문장에서 빠져나와 다음 작업을 시작한다.

# 반복문
일정한 처리를 한 다음 원래 위치로 돌아가 똑같은 처리를 반복하는 처리를 표현

## while문
조건만 맞아떨어지면 일정한 처리를 계속 반복해서 실행.

```js
let i = 0;
while(i<5) {
  //위 괄호의 값이 'true'인 동안에는 안쪽의 코드를 반복해서 실행한다.
  console.log(`i의 값: ${i}`)
  i++; //갱신
}
```

## Big-O 표기법과 시간 복잡도
```js
function binarySearch(x,a) {
  let n = a.length;
  let left = 0, right = n-1;
  while(left<right) {
    let middle = Math.floor((left+right)/2)
    if(x<=a[middle]) {
      right = middle;
      console.log(right)
    } else {
      left = middle + 1
      console.log(left)
    }
  }
  if(x == a[right]) return right;
  return null;
}
let a = [2,4,7,12,15,21,34,35,46,57,70,82,86,92,99]
console.log(binarySearch(46,a))

```

## do/while 문
- do/while 문은 반복해서 실행할지를 마지막 부분에서 판단한다. 
- while문 안에 있는 문장은 한 번도 실행되지 않을 수 있지만 do/while문 안에 있는 `문장은 반드시 한 번 이상 실행`된다.
- while 문과 마찬가지로 do/while 문 안에서는 break문과 contineu문을 사용할 수 있다.

```js
function fact(n) {
  let k = 1, i=n;
  do {
    k*= i--;
  } while(i>0)
  return k;
}

fact(5);
```

## for 문
```
for(초기화식, 조건식, 반복식) 문장
```
- for 문을 실행하면 반복문을 시작하기 전에 초기화식을 단 한번 실행
- 그 후에 반복 작업을 시작하는데 이때 조건식을 먼저 평가
- 조건식을 평가한 결과가 true면 문장을 실행한 후에 반복식을 실행
- 그리고 다시 한번 for문의 시작 부분으로 돌아가서 조건식을 평가

```js
for(let i=0;i<10;i++) {
  console.log(i);
}
```
1. 먼저 변수 i를 선언하고 0으로 초기화
2. 그 후에 반복문을 시작. i<10을 만족하면 반복해서 실행
3. 반복문 안의 console.log(i)가 실행되어 콘솔에는 i값이 출력
4. 반복문 끝의 i++가 실행되어 i값이 1증가
5. i = 10이면 반복문에서 빠져나오고 for 문의 처리가 끝난다.

```js
for(let i =0,j=10; i<11;i++,j--) {
  console.log(i,j)
}
// (0,10),(1,9),(2,8),(3,7),(4,6),(5,5),(6,4),(7,3),(8,2),(9,1),(10,0),(11,-1)
```
배열 요소 합계
```js
function sumArray(a) {
  const sum = 0
  for(let i=0;i<a.length;i++) {
    sum += a[i]
  }
  return sum;
}
const a = [1,2,3,4,5]
console.log(sumArray(a))
```
피타고라스의 수 구하기
```js
const n = 20;
for(let a = 1;a<=n;a++) {
  for(let b = 1;b<=n;b++) {
    for(let c = 1;c<=n;c++) {
      if(a*a + b*b == c*c) {
        console.log(`${a}^2 + ${b}^2 = ${c}^2`)
      }
    }
  }
}
```

## for/in문
- 객체 안의 프로퍼티를 순회하는 반복문. 
- for/in 문이 실행되면 객체 표현식을 평가
- 객체 표현식이 null 또는 undefined로 평가되면 for/in 문을 빠져나와 다음 작업으로 이동
- 객체 표현식이 객체로 평가되면 객체의 프로퍼티 이름이 차례대로 변수에 할당되고 각각의 프로퍼티에 대해서 문장이 한 번씩 실행

```js
const obj = {a:1,b:2,c:3}
for(let p in obj) {
  console.log(`p= ${p}`)
}
// p= a,p= b,p= c
```
for/in문은 프로퍼티 이름만 꺼내 변수에 할당

```js
const obj = {a:1,b:2,c:3}
for(let p in obj) {
  console.log(`obj.${p}= ${obj[p]}`)
}
```
반복문 안에서 프로퍼티 값을 가져오려면 괄호 연산자를 사용해야 한다.

<br>

# 점프문
프로그램의 다른 위치로 이동하는 제어구문.

## 라벨문
`라벨 이름`에는 모든 식별자를 사용할 수 있다. 자바스크립트에서 라벨로 점프할 수 있는 문장은 `break`문과 `continue`문 뿐이다. 실제로 라벨을 붙여서 사용할 수 있는 문장은 `switch`문과 `반복문`뿐이다.

## break 문
```
break 라벨 이름;
```
라벨을 지정한 break 문을 실행하면 라벨이 붙은 문장 끝으로 점프한다.

```js
const a = [2,4,6,8,10], b = [1,3,5,6,9,11] 
loop: for(let i=0;i<a.length;i++){
    for(let j=0;j<b.length;j++) {
      if(a[i] == b[j]) 
      console.log("a["+i+"] = b["+j+"]")
    }
}
```
## continue 문
```
continue 라벨이름;
```
continue 문을 실행하면 반복문 실행을 멈추고 반복을 새로 시작되며 동작이 반복문에 따라 달라진다.

```
while 문 : 반복문의 처음으로 되돌아가서 조건식을 다시 평가. 그결과가 true면 반복문을 처음부터 실행
do/while 문 : 중간을 건너뛰고 반복문의 마지막 조건식을 평가. 그 결과가 true면 반복문을 처음부터 실행
for 문 : 반복식을 실행한 후에 조건식을 평가. 그 결과가 true면 반복문을 이어서 실행
for/in 문 : 반복문의 처음으로 되돌아간다. 지정한 변수에 할당되어 있는 프로퍼티의 다음 프로퍼티를 대상으로 작업을 시작
```

```js
// 배열 a안에서 값이 0 이상인 요소의 값을 모두 더한다.
let a = [2,5,-1,7,-3,6,9]
for(let i=0,sum=0;i<a.length;i++){
  if(a[i]<0)continue;
  sum += a[i];
}
console.log(sum);
```

