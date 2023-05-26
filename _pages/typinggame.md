---
layout: page
title: Typing Game
permalink: /typinggame/
---

<html>
<head>
  <style>
    body {
      text-align: center;
      font-family: Arial, sans-serif;
    }
    #game-container {
      width: 400px;
      margin: 0 auto;
    }
    #word-display {
      font-size: 24px;
      margin-bottom: 20px;
    }
    #input-field {
      font-size: 18px;
      padding: 5px;
      width: 100%;
      box-sizing: border-box;
    }
    #timer {
      font-size: 18px;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div id="game-container">
    <p id="word-display">Start typing...</p>
    <input type="text" id="input-field" autofocus>
    <p id="timer"></p>
  </div>

  <script>
    var words = ["apple", "banana", "cherry", "date", "elderberry", "fig", "grape"];
    var currentWordIndex = 0;
    var currentWord = words[currentWordIndex];
    var startTime = null;
    var timerInterval = null;

    var wordDisplay = document.getElementById("word-display");
    var inputField = document.getElementById("input-field");
    var timer = document.getElementById("timer");

    wordDisplay.textContent = currentWord;

    inputField.addEventListener("input", function(event) {
      var enteredText = event.target.value;

      if (!startTime) {
        startTime = new Date();
        startTimer();
      }

      if (enteredText === currentWord) {
        currentWordIndex++;
        if (currentWordIndex >= words.length) {
          wordDisplay.textContent = "You Win!";
          inputField.style.display = "none";
          stopTimer();
        } else {
          currentWord = words[currentWordIndex];

          wordDisplay.textContent = currentWord;
          inputField.value = "";
        }
      }
    });

    function startTimer() {
      timerInterval = setInterval(updateTimer, 10); // Update every hundredth of a second (10 milliseconds)
    }

    function stopTimer() {
      clearInterval(timerInterval);
    }

    function updateTimer() {
      var currentTime = new Date();
      var elapsedTime = Math.floor((currentTime - startTime) / 10); // Calculate elapsed time in hundredths of a second
      timer.textContent = "Time: " + (elapsedTime / 100).toFixed(2) + " seconds"; // Convert elapsed time to seconds with two decimal places
    }
  </script>
</body>
</html>