---
layout: page
title: Calculator
description: calculator
permalink: /calculator/
---

{% include nav/home.html %}

✨beginning of my calculator page✨


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .calculator {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        #display {
            width: 100%;
            height: 40px;
            font-size: 24px;
            text-align: right;
            padding: 5px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 60px;
            height: 60px;
            font-size: 24px;
            margin: 5px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #e0e0e0;
        }
        /* Button Colors */
        .number {
            background-color: #d9f0ff; /* Light blue */
        }
        .operator {
            background-color: #e0baff; /* Light purple */
        }
        .equals {
            background-color: #f3f4f7; /* White */
            height: 130px;
        }
        .equals:hover, .number:hover, .operator:hover {
            filter: brightness(1.1); /* Slight hover brightness */
        }
    </style>
</head>
<body>

    <div class="calculator">
        <input type="text" id="display" disabled>
        <div>
            <button onclick="clearDisplay()" class="operator">C</button>
            <button onclick="appendToDisplay('7')" class="number">7</button>
            <button onclick="appendToDisplay('8')" class="number">8</button>
            <button onclick="appendToDisplay('9')" class="number">9</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
        </div>
        <div>
            <button onclick="appendToDisplay('4')" class="number">4</button>
            <button onclick="appendToDisplay('5')" class="number">5</button>
            <button onclick="appendToDisplay('6')" class="number">6</button>
            <button class="operator" onclick="appendToDisplay('*')">*</button>
        </div>
        <div>
            <button onclick="appendToDisplay('1')" class="number">1</button>
            <button onclick="appendToDisplay('2')" class="number">2</button>
            <button onclick="appendToDisplay('3')" class="number">3</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
        </div>
        <div>
            <button onclick="appendToDisplay('0')" class="number">0</button>
            <button onclick="calculateResult()" class="equals">=</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
        </div>
    </div>

    <script>
        function appendToDisplay(value) {
            document.getElementById("display").value += value;
        }

        function clearDisplay() {
            document.getElementById("display").value = '';
        }

        function calculateResult() {
            const display = document.getElementById("display");
            try {
                display.value = eval(display.value);
            } catch (error) {
                display.value = 'Error';
            }
        }
    </script>

</body>
</html>
