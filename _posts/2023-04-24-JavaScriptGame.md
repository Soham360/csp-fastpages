<html>
  <head>
    <title>Guess the Number Game</title>
  </head>
  <body>
    <h1>Guess the Number Game</h1>
    <p>I'm thinking of a number between 1 and 100. Can you guess it?</p>
    <input type="text" id="guess">
    <button onclick="checkGuess()">Guess</button>
    <p id="message"></p>

    <script>
      // Generate a random number between 1 and 100
      const randomNumber = Math.floor(Math.random() * 100) + 1;

      // Function to check the user's guess
      function checkGuess() {
        const guessInput = document.getElementById("guess");
        const guess = parseInt(guessInput.value);
        const message = document.getElementById("message");

        if (isNaN(guess) || guess < 1 || guess > 100) {
          message.textContent = "Please enter a valid number between 1 and 100.";
        } else if (guess === randomNumber) {
          message.textContent = "Congratulations! You guessed the correct number!";
        } else if (guess < randomNumber) {
          message.textContent = "Too low! Try again.";
        } else if (guess > randomNumber) {
          message.textContent = "Too high! Try again.";
        }

        // Clear the input field
        guessInput.value = "";
      }
    </script>
  </body>
</html>
