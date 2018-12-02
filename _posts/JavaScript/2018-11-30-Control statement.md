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


