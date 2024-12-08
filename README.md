<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stylish Calculator</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background: linear-gradient(135deg, #6a11cb, #2575fc);
            color: #fff;
        }
        .calculator {
            background: #1e1e2f;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
            width: 320px;
        }
        .display {
            width: 100%;
            height: 60px;
            font-size: 1.8em;
            text-align: right;
            margin-bottom: 20px;
            padding: 10px;
            border: none;
            border-radius: 10px;
            background: #27293d;
            color: #fff;
            outline: none;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
        }
        .button {
            padding: 20px;
            font-size: 1.2em;
            font-weight: bold;
            background: #313552;
            color: #fff;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: background 0.3s, transform 0.2s;
        }
        .button:hover {
            background: #4a4f7c;
        }
        .button:active {
            transform: scale(0.95);
        }
        .button.operator {
            background: #ff5722;
        }
        .button.operator:hover {
            background: #ff784e;
        }
        .button.clear {
            background: #e91e63;
        }
        .button.clear:hover {
            background: #f06292;
        }
        .button.equal {
            background: #4caf50;
            grid-column: span 2;
        }
        .button.equal:hover {
            background: #66bb6a;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" class="display" disabled>
        <div class="buttons">
            <button class="button" onclick="appendNumber('7')">7</button>
            <button class="button" onclick="appendNumber('8')">8</button>
            <button class="button" onclick="appendNumber('9')">9</button>
            <button class="button operator" onclick="appendOperator('/')">÷</button>

            <button class="button" onclick="appendNumber('4')">4</button>
            <button class="button" onclick="appendNumber('5')">5</button>
            <button class="button" onclick="appendNumber('6')">6</button>
            <button class="button operator" onclick="appendOperator('*')">×</button>

            <button class="button" onclick="appendNumber('1')">1</button>
            <button class="button" onclick="appendNumber('2')">2</button>
            <button class="button" onclick="appendNumber('3')">3</button>
            <button class="button operator" onclick="appendOperator('-')">−</button>

            <button class="button" onclick="appendNumber('0')">0</button>
            <button class="button" onclick="appendNumber('.')">.</button>
            <button class="button clear" onclick="clearDisplay()">C</button>
            <button class="button operator" onclick="appendOperator('+')">+</button>

            <button class="button equal" onclick="calculateResult()">=</button>
        </div>
    </div>

    <script>
        let display = document.getElementById('display');

        function appendNumber(number) {
            display.value += number;
        }

        function appendOperator(operator) {
            const lastChar = display.value.slice(-1);
            if ("+-*/".includes(lastChar)) return;
            display.value += operator;
        }

        function clearDisplay() {
            display.value = '';
        }

        function calculateResult() {
            try {
                display.value = eval(display.value.replace(/÷/g, '/').replace(/×/g, '*')) || '';
            } catch {
                display.value = 'Error';
            }
        }
    </script>
</body>
</html>

