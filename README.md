<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <style>
        /* Basic CSS Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
            font-family: Arial, sans-serif;
        }

        .calculator {
            background-color: #4DA6FF;
            border-radius: 10px;
            padding: 20px;
            width: 300px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        .display {
            background-color: white;
            height: 50px;
            width: 100%;
            border-radius: 5px;
            text-align: right;
            padding: 10px;
            font-size: 1.5rem;
            margin-bottom: 20px;
            box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.1);
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        .buttons button {
            padding: 20px;
            font-size: 1.2rem;
            border-radius: 5px;
            border: none;
            background-color: #f1f1f1;
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
            cursor: pointer;
        }

        .buttons button:hover {
            background-color: #e0e0e0;
        }

        .buttons .operator {
            background-color: #ffcc00;
        }

        .buttons .operator:hover {
            background-color: #ffb700;
        }

        .buttons .equals {
            background-color: #00cc66;
            grid-column: span 2;
        }

        .buttons .equals:hover {
            background-color: #00b359;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button onclick="clearDisplay()">C</button>
            <button onclick="deleteLast()">DEL</button>
            <button onclick="appendToDisplay('/')">/</button>
            <button onclick="appendToDisplay('')"></button>
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button onclick="appendToDisplay('-')">-</button>
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('+')">+</button>
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="calculateResult()" class="equals">=</button>
            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
        </div>
    </div>

    <script>
        let display = document.getElementById('display');

        function clearDisplay() {
            display.textContent = '0';
        }

        function deleteLast() {
            if (display.textContent.length > 1) {
                display.textContent = display.textContent.slice(0, -1);
            } else {
                display.textContent = '0';
            }
        }

        function appendToDisplay(value) {
            if (display.textContent === '0') {
                display.textContent = value;
            } else {
                display.textContent += value;
            }
        }

        function calculateResult() {
            try {
                display.textContent = eval(display.textContent);
            } catch {
                display.textContent = 'Error';
            }
        }
    </script>
</body>
</html>
