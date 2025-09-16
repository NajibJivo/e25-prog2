# Guess My Number – Exercise

In this exercise, you will build a fully interactive "Guess My Number" game using JavaScript, HTML, and CSS.

## Goal
Create a game where the computer picks a random number between two values (e.g., 1 and 100), and the user tries to guess it. The game should give feedback after each guess and track the number of attempts.

## Requirements

1. **Random Number**
	- When the page loads or the game restarts, generate a new random number between a minimum and maximum value.
	- Display the range to the user.

2. **User Input**
	- Provide an input field for the user to enter their guess.
	- Make sure the input only allows numbers within the valid range.

3. **Feedback**
	- After each guess, display feedback:
	  - If the guess is too high or too low, tell the user.
	  - If the guess is correct, congratulate the user and show how many attempts it took.
	- Show the number of attempts so far.

4. **Game End and Restart**
	- When the user guesses correctly, display a message (e.g., "Congratulations! You guessed the number!") disable further guesses and show a "Restart" button.
	- When the user clicks "Restart", reset the game state and pick a new number.

## Hints

- Use `Math.random()` and `Math.floor()` to generate the random number.
- Use functions to separate concerns. For example, you might create functions like:
	- `initGame` (set up or reset the game)
	- `handleGuess` (process a guess)
	- `showFeedback` (display messages to the user)
	- `updateAttempts` (show the number of attempts)
	- `endGame` (handle what happens when the game is won)
- Use `textContent` to update feedback and attempt count in the DOM.
- Use `preventDefault()` on the form submit event to avoid page reloads.

## Stretch Goals (Optional)

- Allow the user to set their own min/max range (updating the random number generation accordingly, and the UI).
- Keep a high score (fewest attempts) using `localStorage`.


## Starter Code

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link rel="stylesheet" href="style.css">
	<title>Guess My Number</title>
</head>
<body>
	<main class="container">
		<h1>Guess My Number!</h1>
		<p class="instructions">I'm thinking of a number between <span id="min">1</span> and <span id="max">100</span>. Can you guess it?</p>
		<form id="guessForm" autocomplete="off">
			<input type="number" id="guessInput" min="1" max="100" placeholder="Enter guess" required>
			<button type="submit">Guess</button>
		</form>
		<p id="feedback"></p>
		<p id="attempts"></p>
		<button id="restartBtn" style="display:none;">Restart Game</button>
	</main>
	<script src="app.js"></script>
</body>
</html>
```
### CSS (style.css)
```css
body {
	background: #f4f6fb;
	min-height: 100vh;
	margin: 0;
	font-family: 'Segoe UI', Arial, sans-serif;
}

.container {
	max-width: 400px;
	margin: 60px auto;
	background: #fff;
	border-radius: 12px;
	box-shadow: 0 4px 16px rgba(0,0,0,0.10);
	padding: 36px 32px 28px 32px;
	text-align: center;
}

h1 {
	color: #2563eb;
	margin-bottom: 18px;
	font-size: 2em;
	letter-spacing: 1px;
}

.instructions {
	color: #444;
	margin-bottom: 24px;
	font-size: 1.1em;
}

#guessForm {
	display: flex;
	gap: 10px;
	justify-content: center;
	margin-bottom: 18px;
}

#guessInput {
	padding: 10px 12px;
	font-size: 1.1em;
	border: 1px solid #bcd0ee;
	border-radius: 5px;
	width: 120px;
	outline: none;
	transition: border 0.2s;
}
#guessInput:focus {
	border: 1.5px solid #2563eb;
}

button {
	padding: 10px 22px;
	font-size: 1.1em;
	border: none;
	border-radius: 5px;
	background: #4f8cff;
	color: #fff;
	cursor: pointer;
	transition: background 0.2s;
}
button:hover {
	background: #2563eb;
}

#feedback {
	min-height: 32px;
	margin: 18px 0 8px 0;
	font-size: 1.15em;
	font-weight: 500;
}
#feedback.info {
	color: #2563eb;
}
#feedback.success {
	color: #1ca97a;
}
#feedback.warning {
	color: #eab308;
}

#attempts {
	color: #888;
	font-size: 1em;
	margin-bottom: 10px;
}

#restartBtn {
	margin-top: 18px;
	background: #ff5c5c;
	color: #fff;
	border: none;
	border-radius: 5px;
	padding: 10px 22px;
	font-size: 1.1em;
	cursor: pointer;
	transition: background 0.2s;
}
#restartBtn:hover {
	background: #d90429;
}

.hidden {
	display: none;
}
```
### JavaScript (app.js)
```javascript
const MIN = 1;
const MAX = 100;
let secretNumber;
let attempts;

// DOM elements to be used:
// const guessForm = document.querySelector("#guessForm");
// const guessInput = document.querySelector("#guessInput");
// const feedback = document.querySelector("#feedback");
// const attemptsDisplay = document.querySelector("#attempts");
// const restartBtn = document.querySelector("#restartBtn");

// TODO
function initGame() {
}
