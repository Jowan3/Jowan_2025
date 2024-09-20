---
layout: page
title: Snake
description: Snake game
permalink: /snake/
---

{% include nav/home.html %}

✨beginning of my snake page✨
 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cute Purple Snake Game</title>
    <!-- Include Comfortaa font -->
    <link href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@300&display=swap" rel="stylesheet">
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0e5f5;
            font-family: 'Comfortaa', cursive; /* Use Comfortaa font */
            margin: 0;
            overflow: hidden; /* Prevent page scroll */
        }

        .game-container {
            border: 5px solid #9b59b6;
            border-radius: 10px;
            padding: 10px;
            background-color: #ffffff;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            text-align: center;
        }

        canvas {
            background-color: #e0d6e8;
        }

        .score {
            font-size: 24px;
            color: #9b59b6;
        }

        button {
            font-family: 'Comfortaa', cursive;
            background-color: #9b59b6;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
            margin-top: 10px;
        }

        button:hover {
            background-color: #8e44ad;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <canvas id="gameCanvas" width="400" height="400"></canvas>
        <div class="score">Score: <span id="score">0</span></div>
        <button id="restartBtn" style="display: none;" onclick="restartGame()">Play Again</button>
    </div>
    <script>
        const canvas = document.getElementById("gameCanvas");
        const ctx = canvas.getContext("2d");
        const box = 20;
        let snake = [{ x: box * 5, y: box * 5 }];
        let direction = { x: 0, y: 0 };
        let fruits = [];
        let score = 0;
        let gameInterval;
        const restartBtn = document.getElementById("restartBtn");

        // Function to generate random fruit position
        function createFruit() {
            const x = Math.floor(Math.random() * (canvas.width / box)) * box;
            const y = Math.floor(Math.random() * (canvas.height / box)) * box;
            fruits.push({ x, y });
        }

        // Disable default arrow key behavior (prevent page scrolling)
        window.addEventListener("keydown", function(event) {
            if (["ArrowUp", "ArrowDown", "ArrowLeft", "ArrowRight"].includes(event.key)) {
                event.preventDefault();
            }
        });

        // Create initial fruits
        for (let i = 0; i < 3; i++) {
            createFruit();
        }

        document.addEventListener("keydown", changeDirection);

        function changeDirection(event) {
            if (event.key === "ArrowUp" && direction.y === 0) {
                direction = { x: 0, y: -1 };
            } else if (event.key === "ArrowDown" && direction.y === 0) {
                direction = { x: 0, y: 1 };
            } else if (event.key === "ArrowLeft" && direction.x === 0) {
                direction = { x: -1, y: 0 };
            } else if (event.key === "ArrowRight" && direction.x === 0) {
                direction = { x: 1, y: 0 };
            }
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Draw the snake
            for (let i = 0; i < snake.length; i++) {
                ctx.fillStyle = i === 0 ? "#8e44ad" : "#9b59b6"; // Head is purple, body is a lighter purple
                ctx.fillRect(snake[i].x, snake[i].y, box, box);
                ctx.strokeStyle = "#6c3483";
                ctx.strokeRect(snake[i].x, snake[i].y, box, box);
            }

            // Draw the fruits (default blocks)
            ctx.fillStyle = "#e74c3c"; // Red color for the fruit
            for (const fruit of fruits) {
                ctx.fillRect(fruit.x, fruit.y, box, box);
                ctx.strokeRect(fruit.x, fruit.y, box, box);
            }

            // Move the snake
            const head = { x: snake[0].x + direction.x * box, y: snake[0].y + direction.y * box };

            // Check for fruit collision
            for (let i = 0; i < fruits.length; i++) {
                if (head.x === fruits[i].x && head.y === fruits[i].y) {
                    score++;
                    document.getElementById("score").innerText = score;
                    fruits.splice(i, 1); // Remove the fruit that was eaten
                    createFruit(); // Add a new fruit
                    break;
                }
            }

            snake.unshift(head);

            // Game over conditions
            if (head.x < 0 || head.x >= canvas.width || head.y < 0 || head.y >= canvas.height || collision(head, snake)) {
                clearInterval(gameInterval);
                alert("Game Over! Your score: " + score);
                restartBtn.style.display = "block"; // Show the replay button
            }
        }

        function collision(head, array) {
            for (let i = 1; i < array.length; i++) {
                if (head.x === array[i].x && head.y === array[i].y) {
                    return true;
                }
            }
            return false;
        }

        function startGame() {
            score = 0;
            snake = [{ x: box * 5, y: box * 5 }];
            direction = { x: 0, y: 0 };
            fruits = [];
            document.getElementById("score").innerText = score;
            restartBtn.style.display = "none";
            for (let i = 0; i < 3; i++) {
                createFruit();
            }
            gameInterval = setInterval(draw, 100);
        }

        function restartGame() {
            startGame(); // Reset and start the game again
        }

        // Start the game when the page loads
        window.onload = startGame;
    </script>
</body>
</html>
