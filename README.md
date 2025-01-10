# Calculator
<!DOCTYPE html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .calculator {
      width: 300px;
      background: #fff;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      overflow: hidden;
    }

    .display {
      background: #222;
      color: #fff;
      font-size: 2rem;
      text-align: right;
      padding: 10px;
      height: 60px;
      box-sizing: border-box;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1px;
    }

    .buttons button {
      background: #f0f0f0;
      border: none;
      padding: 20px;
      font-size: 1.2rem;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    .buttons button:hover {
      background: #ddd;
    }

    .buttons .operator {
      background: #ffc107;
    }

    .buttons .operator:hover {
      background: #e0a800;
    }

    .buttons .equals {
      background: #28a745;
      grid-column: span 2;
    }

    .buttons .equals:hover {
      background: #218838;
    }

    .buttons .clear {
      background: #dc3545;
      grid-column: span 2;
    }

    .buttons .clear:hover {
      background: #c82333;
    }
  </style>
</head>
<body>

  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <!-- Number Buttons -->
      <button onclick="appendNumber('7')">7</button>
      <button onclick="appendNumber('8')">8</button>
      <button onclick="appendNumber('9')">9</button>
      <button class="operator" onclick="setOperator('/')">/</button>
      
      <button onclick="appendNumber('4')">4</button>
      <button onclick="appendNumber('5')">5</button>
      <button onclick="appendNumber('6')">6</button>
      <button class="operator" onclick="setOperator('*')">*</button>
      
      <button onclick="appendNumber('1')">1</button>
      <button onclick="appendNumber('2')">2</button>
      <button onclick="appendNumber('3')">3</button>
      <button class="operator" onclick="setOperator('-')">-</button>
      
      <button onclick="appendNumber('0')">0</button>
      <button onclick="appendDecimal()">.</button>
      <button class="equals" onclick="calculate()">=</button>
      <button class="operator" onclick="setOperator('+')">+</button>
      
      <button class="clear" onclick="clearDisplay()">C</button>
    </div>
  </div>

  <script>
    let currentInput = '';
    let previousInput = '';
    let operator = null;

    const display = document.getElementById('display');

    function appendNumber(number) {
      if (currentInput.includes('.') && number === '.') return; // Prevent multiple decimals
      currentInput += number;
      updateDisplay();
    }

    function setOperator(op) {
      if (currentInput === '') return; // Ignore if no input
      if (previousInput !== '') calculate(); // Calculate if operator already exists
      operator = op;
      previousInput = currentInput;
      currentInput = '';
    }

    function appendDecimal() {
      if (!currentInput.includes('.')) currentInput += '.';
      updateDisplay();
    }

    function calculate() {
      if (previousInput === '' || currentInput === '') return; // Ensure valid inputs
      let result;
      const prev = parseFloat(previousInput);
      const current = parseFloat(currentInput);
      switch (operator) {
        case '+':
          result = prev + current;
          break;
        case '-':
          result = prev - current;
          break;
        case '*':
          result = prev * current;
          break;
        case '/':
          result = current === 0 ? 'Error' : prev / current; // Handle divide by zero
          break;
        default:
          return;
      }
      currentInput = result.toString();
      operator = null;
      previousInput = '';
      updateDisplay();
    }

    function clearDisplay() {
      currentInput = '';
      previousInput = '';
      operator = null;
      updateDisplay();
    }

    function updateDisplay() {
      display.innerText = currentInput || '0';
    }
  </script>

</body>
</html>
