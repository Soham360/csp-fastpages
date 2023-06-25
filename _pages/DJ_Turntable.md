---
layout: page
title: DJ Turntable
permalink: /turntable/
---

<html>
<head>
  <title>Virtual DJ Turntable</title>
  <style>
    .turntable {
      width: 400px;
      height: 400px;
      position: relative;
      border: 2px solid #333;
      border-radius: 50%;
      overflow: hidden;
      margin: 0 auto;
    }
    .record {
      width: 100%;
      height: 100%;
      background-color: #333;
      border-radius: 50%;
    }
    .record-label {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 70%;
      height: 70%;
      background-color: #fff;
      border-radius: 50%;
    }
    .record-label img {
      display: block;
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 50%;
    }
    .controls {
      text-align: center;
      margin-top: 20px;
    }
    .button {
      display: inline-block;
      padding: 10px 20px;
      background-color: #333;
      color: #fff;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
      margin: 0 10px;
    }
  </style>
</head>
<body>
  <div class="turntable">
    <div class="record">
      <div class="record-label">
        <img src="https://github.com/Soham360/csp-fastpages/blob/master/images/record.png?raw=true" alt="Record Image">
      </div>
    </div>
  </div>
  <div class="controls">
    <button class="button">Play</button>
    <button class="button">Stop</button>
  </div>

  <script>
    var audio = new Audio('https://github.com/Soham360/csp-fastpages/blob/master/images/HeartOnMySleeve.mp3?raw=true');
    var isPlaying = false;

    function togglePlayback() {
      if (isPlaying) {
        audio.pause();
      } else {
        audio.play();
      }
      isPlaying = !isPlaying;
    }

    document.querySelector('.button').addEventListener('click', togglePlayback);
  </script>
</body>
</html>
