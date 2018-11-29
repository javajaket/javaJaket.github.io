---
layout: post
title: '[Codility] stop watch'
excerpt: 
category: Algorithm
tags:
  - Algorithm
  - Codility
  - stop watch
---

스톱워치

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>stop watch</title>
  <script>
    window.onload = function() {
      let startButton = document.getElementById('start')
      let stopButton = document.getElementById('stop')
      let display = document.getElementById('display')
      let startTime,timer

      startButton.onclick = start;
      function start() {
        startButton.onclick = null
        stopButton.onclick = stop
        startTime = new Date()
        timer = setInterval(function() {
          let now = new Date()
          display.innerHTML = ((now - startTime)/1000).toFixed(2)
        },10)    
      }
      function stop() {
        clearInterval(timer);
        startButton.onclick = start;
      }
    };
  </script>
</head>
<body>
  <p id="display">0.00</p>
  <input type="button" value="start" id="start">
  <input type="button" value="stop" id="stop">
</body>
</html>
```