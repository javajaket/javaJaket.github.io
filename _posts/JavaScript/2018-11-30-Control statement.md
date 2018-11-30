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
if(hp<120 && lp<80) {
  judgement.innerHTML = '정상';
} else if(139>hp && 89>lp) {
  judgement.innerHTML = '불안';
} else {
  judgement.innerHTML = '비정상';
}
```

