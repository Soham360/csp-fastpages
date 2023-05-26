---
layout: page
title: Typing Game
permalink: /nitrotype/
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
  </style>
</head>
<body>
  <div id="game-container">
    <p id="word-display">Start typing...</p>
    <input type="text" id="input-field" autofocus>
  </div>

  <script>
    var words = ["apple", "banana", "cherry", "date", "elderberry", "fig", "grape"];
    var currentWordIndex = 0;
    var currentWord = words[currentWordIndex];

    var wordDisplay = document.getElementById("word-display");
    var inputField = document.getElementById("input-field");

    wordDisplay.textContent = currentWord;

    inputField.addEventListener("input", function(event) {
      var enteredText = event.target.value;

      if (enteredText === currentWord) {
        currentWordIndex++;
        if (currentWordIndex >= words.length) {
            wordDisplay.textContent = "You Win!";
        } else {
            currentWord = words[currentWordIndex];

            wordDisplay.textContent = currentWord;
            inputField.value = "";
        }
      }
    });
  </script>
</body>
</html>