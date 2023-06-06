---
layout: page
title: Typing Game
permalink: /typinggame/
---

<html>
<head>
  <style>
    /* styling */
    body {
      text-align: center;
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
    .result {
    border-radius: 12px;
    border: 1px solid black;
    padding: 20px;
    max-width: 300px;
    flex-shrink: 0;
    }
  </style>
  <!-- Importing table and sorting code -->
  <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
  <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script>var define = null;</script>
  <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>
<body>
  <!-- div for the game. Includes the words being displayed, the inputs, and the timer -->
  <div id="game-container">
    <p id="word-display">Start typing...</p>
    <input type="text" id="input-field" autofocus>
    <p id="timer"></p>
  </div>
  <!-- This is the leaderboard table. The table headers are given here and the contents are in "flaskBody" and is updated by the script at the bottom. -->
  <div id="result">
    <table id="flaskTable" class="table" style="width:100%">
        <thead id="flaskHead">
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Time</th>
            </tr>
        </thead>
        <tbody id="flaskBody"></tbody>
    </table>
  </div>

 

  <script>
    // This is the word bank
    var words = ["determine", "retiree", "thought", "improve", "truth", "active", "polish", "curve", "stun", "addicted", "extreme", "affect", "present", "certain", "dramatic", "greeting", "order", "twin", "fade", "relevance", "glimpse", "grain", "debt", "tell", "morning", "genetic", "suggest", "reduce", "demonstrate", "lift", "make", "entry", "circulation", "supply", "accountant", "admire", "spot", "assignment", "bracket", "satellite", "agony", "equal", "afford", "wash", "throw", "mistreat", "measure", "competition", "education", "tolerate"];
    // This is the counter for how many words have been completed
    var wordsComplete = 0;
    // This generates a random integer from 1 to 50
    var currentWordIndex = Math.floor((Math.random() * 50) + 1);
    // This uses the random integer from above as an index for a random word from the word bank
    var currentWord = words[currentWordIndex];
    // This sets the startTime and the timerInterval to un undefined value
    var startTime = null;
    var timerInterval = null;

    // This is the table being defined as a constant variable
    const tableContainer = document.getElementById("result");

    // This sets the username and the actualTime to un undefined value
    var username = null;
    var actualTime = null;

    // This is the code that replaces the previous word
    var wordDisplay = document.getElementById("word-display");
    // This gets the input from the text box
    var inputField = document.getElementById("input-field");
    // This is the code that allows the timer to update
    var timer = document.getElementById("timer");

    // This is the database where the scores are stored. The read and create urls are also defined here
    const url = "https://petitepandas.duckdns.org/api/times"
    const create_fetch = url + '/create';
    const read_fetch = url + '/';

    // This displays the random word
    wordDisplay.textContent = currentWord;

    // function starts as soon as it detects an input
    inputField.addEventListener("input", function(event) {
      var enteredText = event.target.value;

      // starts the timer after the user inputs something into the textbox
      if (!startTime) {
        startTime = new Date();
        startTimer();
      }

      // verifies is the entered word is the same as the actual word they are trying to type
      if (enteredText === currentWord) {
        currentWordIndex = Math.floor((Math.random() * 50) + 1);
        wordsComplete++;
        // makes sure the user has typed at least 5 random words
        if (wordsComplete >= 5) {
          // displays a "You Win!"
          wordDisplay.textContent = "You Win!";
          // hides the text box
          inputField.style.display = "none";
          // stops the timer
          stopTimer();
        } else {
          // if the user has not typed 5 words, gets another random word
          currentWord = words[currentWordIndex];
          // displays the random word
          wordDisplay.textContent = currentWord;
          // clears the text box
          inputField.value = "";
        }
      }
    });

    // starts repeated action (timer) that updates every 10 milliseconds (0.01)
    function startTimer() {
      timerInterval = setInterval(updateTimer, 10);
    }

    // stops the timer when it is called. It is called after the user has typed 5 words
    function stopTimer() {
      // makes the action above (timer) stop 
      clearInterval(timerInterval);
      // alert(timer.textContent)
      setTimeout(()=> {
         username = prompt('What is your name?');
         create_times();
        //  onPageLoad();
        setTimeout(()=> {
          location.reload();
        }
        ,1000);
      }
      ,1000);
    }

    function updateTimer() {
      var currentTime = new Date();
      var elapsedTime = Math.floor((currentTime - startTime) / 10); // Calculate elapsed time in hundredths of a second
      actualTime = (elapsedTime / 100).toFixed(2)
      timer.textContent = "Time: " + actualTime + " seconds"; // Convert elapsed time to seconds with two decimal places
    }

    function create_times(){
        // New data entry
        const body = {
            uid: username,
            totaltime: actualTime,
        };
        const requestOptions = {
            method: 'POST',
            body: JSON.stringify(body),
            headers: {
                "content-type": "application/json",
                'Authorization': 'Bearer my-token',
            },
        };
        // URL for Create API
        // Fetch API call to the database to create a new review
        fetch(create_fetch, requestOptions)
        .then(response => {
            // trap error response from Web API
            // response contains valid result
            response.json().then(data => {
                console.log(data);
                // tableContainer.innerHTML = ''
            })
        })
    }

  $(document).ready(function() {
  // When document is ready...
  // $(function(){
  //     onPageLoad();
  // });

  // function onPageLoad(){

    fetch('https://petitepandas.duckdns.org/api/times/', { mode: 'cors' })
    .then(response => {
      if (!response.ok) {
        throw new Error('API response failed');
      }
      return response.json();
    })
    .then(data => {
      for (const row of data) {
        // BUG warning/resolution - DataTable requires row to be single append
        $('#flaskBody').append('<tr><td>' + 
            row.id + '</td><td>' + 
            row.uid + '</td><td>' + 
            row.totaltime + '</td></tr>');
      }
      // BUG warning - Jupyter does not show Datatable controls, works on deployed GitHub pages
      $("#flaskTable").DataTable();
    })
    .catch(error => {
      console.error('Error:', error);
    });
  });
  </script>
</body>
</html>