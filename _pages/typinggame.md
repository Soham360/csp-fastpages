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
  <!-- load jQuery and DataTables syle and scripts -->
  <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
  <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script>var define = null;</script>
  <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>
<body>
  <div id="game-container">
    <p id="word-display">Start typing...</p>
    <input type="text" id="input-field" autofocus>
    <p id="timer"></p>
  </div>
  <div id="result">
  </div>

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

  <script>
    var words = ["apple"]; //, "banana", "cherry", "date", "elderberry", "fig", "grape"];
    var currentWordIndex = 0;
    var currentWord = words[currentWordIndex];
    var startTime = null;
    var timerInterval = null;

    var username = null;

    var wordDisplay = document.getElementById("word-display");
    var inputField = document.getElementById("input-field");
    var timer = document.getElementById("timer");

    const url = "http://127.0.0.1:8086/api/times"
    const resultContainer = document.getElementById("result");
    const create_fetch = url + '/create';
    const read_fetch = url + '/';

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
      // alert(timer.textContent)
      setTimeout(()=> {
         username = prompt('What is your name?');
         create_times()
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
        alert(username)
        alert(actualTime)  
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
        alert(create_fetch)
        alert(requestOptions)
        fetch(create_fetch, requestOptions)
        .then(response => {
            // trap error response from Web API
            // response contains valid result
            response.json().then(data => {
                console.log(data);
            })
        })
    }

  $(document).ready(function() {
    fetch('http://127.0.0.1:8086/api/times/', { mode: 'cors' })
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