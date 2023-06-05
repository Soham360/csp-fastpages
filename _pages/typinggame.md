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
</head>
<body>
  <div id="game-container">
    <p id="word-display">Start typing...</p>
    <input type="text" id="input-field" autofocus>
    <p id="timer"></p>
  </div>
  <div id="result">
  </div>

  <script>
    var words = ["apple", "banana", "cherry", "date", "elderberry", "fig", "grape"];
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

    read_times();

    function read_times() {
        // prepare fetch options
        const read_options = {
        method: 'GET',
        mode: 'cors',
        cache: 'default',
        credentials: 'omit',
        headers: {
            'Content-Type': 'application/json'
        },        
        };
        // fetch the data from API
        fetch(read_fetch, read_options)
        // response is a RESTful "promise" on any successful fetch
        .then(response => {
            // check for response errors
            if (response.status !== 200) {
                const errorMsg = 'Database read error: ' + response.status;
                console.log(errorMsg);
                return;
            }
            // valid response will have json data
            response.json().then(data => {
                console.log(data);
                resultContainer.innerHTML = ''
                //Construct Table header
                const tbody = document.createElement("tbody");
                const tr = document.createElement("tr");
                const col1 = document.createElement("td");
                const col2 = document.createElement("td")
                // obtain data that is specific to the API
                col1.innerHTML = "<span style='font-weight:bold' onclick='sortTable(0)'>Username</span>";
                col2.innerHTML = "<span style='font-weight:bold' onclick='sortTable(1)'>Time</span>";
                // add HTML to container
                tr.appendChild(col1);
                tr.appendChild(col2);                 
                resultContainer.appendChild(tr);
                //Print Reviews              
                for (let row in data) {
                console.log(data[row]);
                add_row(data[row]);
                }
            })
        })
        // catch fetch errors (ie ACCESS to server blocked)
        .catch(err => {
        console.error(err);
        alert(err);
        });
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
        fetch(create_fetch, requestOptions)
        .then(response => {
            // trap error response from Web API
            // response contains valid result
            response.json().then(data => {
                console.log(data);
                //add a table row for the new/created reviewid
                add_row(data);
            })
        })
    }
    function add_row(data) {
        const tr = document.createElement("tr");
        const uid = document.createElement("td");  
        const totaltime = document.createElement("td");
        // obtain data that is specific to the API
        // alert(data.uid)
        // alert(data.totaltime)
        uid.innerHTML = data.uid;   
        totaltime.innerHTML = data.totaltime;
        // add HTML to container
        tr.appendChild(uid);  
        tr.appendChild(totaltime);
        resultContainer.appendChild(tr);
    }

    function sortTable(columnIndex) {
      const table = document.getElementById("result");
      const tbody = table.getElementsByTagName("tbody")[0];
      alert("sort table" + columnIndex + tbody)
      const rows = tbody.getElementsByTagName("tr");
      const sortDirection = getSortDirection(columnIndex);

      const sortedRows = Array.from(rows)
        .sort((rowA, rowB) => {
          const cellA = rowA.getElementsByTagName("td")[columnIndex];
          const cellB = rowB.getElementsByTagName("td")[columnIndex];
          return compareCells(cellA, cellB, sortDirection);
        });

      for (const row of sortedRows) {
        tbody.appendChild(row);
      }
    }

    function getSortDirection(columnIndex) {
      const table = document.getElementById("result");
      const headerRow = table.getElementsByTagName("thead")[0].getElementsByTagName("tr")[0];
      const headerCell = headerRow.getElementsByTagName("th")[columnIndex];

      if (headerCell.getAttribute("data-sort-direction") === "asc") {
        headerCell.setAttribute("data-sort-direction", "desc");
        return "desc";
      } else {
        headerCell.setAttribute("data-sort-direction", "asc");
        return "asc";
      }
    }

    function compareCells(cellA, cellB, sortDirection) {
      const valueA = cellA.textContent.trim();
      const valueB = cellB.textContent.trim();

      if (sortDirection === "asc") {
        if (valueA < valueB) {
          return -1;
        } else if (valueA > valueB) {
          return 1;
        } else {
          return 0;
        }
      } else {
        if (valueA < valueB) {
          return 1;
        } else if (valueA > valueB) {
          return -1;
        } else {
          return 0;
        }
      }
    }
  </script>
</body>
</html>