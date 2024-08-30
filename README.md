<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora Avanzada</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }

        .calculator {
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
            overflow: hidden;
            width: 250px;
        }

        #display {
            width: 100%;
            padding: 10px;
            border: none;
            border-bottom: 1px solid #ccc;
            font-size: 24px;
            text-align: right;
            box-sizing: border-box;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
        }

        button {
            padding: 20px;
            font-size: 18px;
            border: 1px solid #ccc;
            background-color: #fff;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        button:hover {
            background-color: #f0f0f0;
        }

        button:active {
            background-color: #e0e0e0;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled>
        <div class="buttons">
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button onclick="appendToDisplay('/')">/</button>
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('*')">*</button>
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="appendToDisplay('-')">-</button>
            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button onclick="calculate()">=</button>
            <button onclick="appendToDisplay('+')">+</button>
            <button onclick="appendToDisplay('sqrt(')">sqrt</button>
            <button onclick="appendToDisplay('pow(')">pow</button>
            <button onclick="appendToDisplay('(')">(</button>
            <button onclick="appendToDisplay(')')">)</button>
            <button onclick="clearDisplay()">C</button>
        </div>
    </div>
    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function calculate() {
            let expression = document.getElementById('display').value;
            
            try {
                // Replace 'sqrt' with 'Math.sqrt' and 'pow' with '**' for exponentiation
                expression = expression.replace(/sqrt\(/g, 'Math.sqrt(');
                expression = expression.replace(/pow\(/g, '**');
                let result = eval(expression);
                document.getElementById('display').value = result;
            } catch (error) {
                document.getElementById('display').value = 'Error';
            }
        }
    </script>
</body>
</html>
