<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator App</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f4f4f4;
      font-family: Arial, sans-serif;
    }

    .calculator {
      width: 260px;
      background: #222;
      padding: 20px;
      border-radius: 10px;
    }

    .display {
      width: 100%;
      height: 50px;
      margin-bottom: 15px;
      background: #000;
      color: #0f0;
      font-size: 1.5em;
      text-align: right;
      padding: 10px;
      border-radius: 5px;
      box-sizing: border-box;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      height: 50px;
      font-size: 1.2em;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button.number {
      background: #444;
      color: white;
    }

    button.operator {
      background: orange;
      color: white;
    }

    button.equal {
      background: green;
      color: white;
      grid-column: span 2;
    }

    button.clear {
      background: red;
      color: white;
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button class="clear" onclick="clearDisplay()">C</button>
      <button class="operator" onclick="appendOperator('/')">÷</button>
      <button class="operator" onclick="appendOperator('*')">×</button>

      <button class="number" onclick="appendNumber(7)">7</button>
      <button class="number" onclick="appendNumber(8)">8</button>
      <button class="number" onclick="appendNumber(9)">9</button>
      <button class="operator" onclick="appendOperator('-')">-</button>

      <button class="number" onclick="appendNumber(4)">4</button>
      <button class="number" onclick="appendNumber(5)">5</button>
      <button class="number" onclick="appendNumber(6)">6</button>
      <button class="operator" onclick="appendOperator('+')">+</button>

      <button class="number" onclick="appendNumber(1)">1</button>
      <button class="number" onclick="appendNumber(2)">2</button>
      <button class="number" onclick="appendNumber(3)">3</button>
      <button class="equal" onclick="calculateResult()">=</button>

      <button class="number" onclick="appendNumber(0)">0</button>
      <button class="number" onclick="appendDot()">.</button>
    </div>
  </div>

  <script>
    let display = document.getElementById("display");
    let currentInput = "0";

    function updateDisplay() {
      display.innerText = currentInput;
    }

    function appendNumber(number) {
      if (currentInput === "0") {
        currentInput = number.toString();
      } else {
        currentInput += number;
      }
      updateDisplay();
    }

    function appendOperator(operator) {
      if (!isNaN(currentInput.slice(-1))) {
        currentInput += operator;
      }
      updateDisplay();
    }

    function appendDot() {
      let lastNumber = currentInput.split(/[\+\-\*\/]/).pop();
      if (!lastNumber.includes(".")) {
        currentInput += ".";
      }
      updateDisplay();
    }

    function clearDisplay() {
      currentInput = "0";
      updateDisplay();
    }

    function calculateResult() {
      try {
        currentInput = eval(currentInput).toString();
      } catch {
        currentInput = "Error";
      }
      updateDisplay();
    }
  </script>
</body>
</html>
