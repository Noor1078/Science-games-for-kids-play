# Science-games-for-kids-play
Science games for kids 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Guess the Planet - Science Game</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="game-container">
    <h1>Guess the Planet</h1>
    <p id="question">Loading...</p>
    <div id="options"></div>
    <p id="result"></p>
    <button onclick="nextQuestion()">Next</button>
  </div>
  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  background: #e0f7fa;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.game-container {
  background: white;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 10px rgba(0,0,0,0.2);
  text-align: center;
}

button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

#options button {
  display: block;
  width: 100%;
  margin: 5px auto;
}
const questions = [
  {
    fact: "This planet is known as the Red Planet.",
    answer: "Mars",
    options: ["Earth", "Mars", "Venus", "Jupiter"]
  },
  {
    fact: "This is the largest planet in our solar system.",
    answer: "Jupiter",
    options: ["Saturn", "Neptune", "Jupiter", "Mars"]
  },
  {
    fact: "This planet has rings made of ice and rock.",
    answer: "Saturn",
    options: ["Earth", "Saturn", "Uranus", "Venus"]
  }
];

let current = 0;

function showQuestion() {
  const q = questions[current];
  document.getElementById('question').innerText = q.fact;
  const optionsDiv = document.getElementById('options');
  optionsDiv.innerHTML = "";

  q.options.forEach(opt => {
    const btn = document.createElement("button");
    btn.innerText = opt;
    btn.onclick = () => checkAnswer(opt);
    optionsDiv.appendChild(btn);
  });

  document.getElementById('result').innerText = "";
}

function checkAnswer(selected) {
  const correct = questions[current].answer;
  if (selected === correct) {
    document.getElementById('result').innerText = "✅ Correct!";
  } else {
    document.getElementById('result').innerText = "❌ Try again!";
  }
}

function nextQuestion() {
  current = (current + 1) % questions.length;
  showQuestion();
}

window.onload = showQuestion;
