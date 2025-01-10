# Calculator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #eef2f3;
    }
    .calculator {
      display: inline-block;
      margin-top: 50px;
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
    .calculator input {
      width: 200px;
      height: 40px;
      font-size: 18px;
      text-align: right;
      margin-bottom: 10px;
    }
    .calculator button {
      width: 50px;
      height: 50px;
      font-size: 18px;
      margin: 5px;
      border: none;
      background-color: #007bff;
      color: white;
      border-radius: 5px;
      cursor: pointer;
    }
    .calculator button:hover {
      background-color: #0056b3;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="result" disabled>
    <br>
    <button onclick="clearResult()">C</button>
    <button onclick="appendValue('/')">/</button>
    <button onclick="appendValue('*')">*</button>
    <button onclick="backspace()">←</button>
    <br>
    <button onclick="appendValue('7')">7</button>
    <button onclick="appendValue('8')">8</button>
    <button onclick="appendValue('9')">9</button>
    <button onclick="appendValue('-')">-</button>
    <br>
    <button onclick="appendValue('4')">4</button>
    <button onclick="appendValue('5')">5</button>
    <button onclick="appendValue('6')">6</button>
    <button onclick="appendValue('+')">+</button>
    <br>
    <button onclick="appendValue('1')">1</button>
    <button onclick="appendValue('2')">2</button>
    <button onclick="appendValue('3')">3</button>
    <button onclick="calculate()">=</button>
  </div>
  <script>
    function appendValue(value) {
      document.getElementById('result').value += value;
    }
    function clearResult() {
      document.getElementById('result').value = '';
    }
    function calculate() {
      try {
        document.getElementById('result').value = eval(document.getElementById('result').value);
      } catch {
        alert('Invalid Input');
      }
    }
    function backspace() {
      let current = document.getElementById('result').value;
      document.getElementById('result').value = current.slice(0, -1);
    }
  </script>
</body>
</html>
