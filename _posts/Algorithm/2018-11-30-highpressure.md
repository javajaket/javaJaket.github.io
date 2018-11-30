---
layout: post
title: '[Codility] highpressure'
excerpt: 
category: Algorithm
tags:
  - Algorithm
  - Codility
  - highpressure
---

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>highpressure confirm</title>
  <script>
    window.onload = function() {
      document.getElementById('button').onclick = function() {
        const hp = parseFloat(document.getElementById('highpressure').value)
        const lp = parseFloat(document.getElementById('lowpressure').value)
        const judgement = document.getElementById('judgement')
        if(hp<120 && lp<80) {
          judgement.innerHTML = '정상';
        } else if(139>hp && 89>lp) {
          judgement.innerHTML = '불안';
        } else {
          judgement.innerHTML = '비정상';
        }
      }
    }
  </script>
</head>
<body>
  <p>수축기 혈압(최고 혈압)<input type="number" value='hp' id='highpressure'></p>
  <p>이완기 혈압(최저 혈압)<input type="number" value='lp' id='lowpressure'></p>
  <p id="judgement">이곳에 판정 결과가 표시됩니다.</p>
  <input type="button" value="확인하기" id="button">
</body>
</html>
```