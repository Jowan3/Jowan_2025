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
    <title>Snake Game</title>
    <style>
        body {
            background-color: #f0f0f0;
        }
        .wrap {
            margin-left: auto;
            margin-right: auto;
        }

        canvas {
            display: block;
            border-style: solid;
            border-width: 10px;
            border-color: #800080; /* Purple border */
            margin: 20px auto;
        }

        canvas:focus {
            outline: none;
        }

        #menu {
            display: block;
            text-align: center;
            font-size: 20px;
        }

        #score_value {
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="pb-3 mb-4 border-bottom border-primary text-dark">
            <p class="fs-4">Snake Score: <span id="score_value">0</span></p>
        </header>
        <canvas id="snake" class="wrap" width="320" height="320" tabindex="1"></canvas>
    </div>

    <script>
        (function() {
            const canvas = document.getElementById("snake");
            const ctx = canvas.getContext("2d");
            const BLOCK = 10;  // Size of each snake block

            let snake = [{ x: 0, y: 15 }];  // Initial snake
            let snake_dir = 1;  // Initial direction (1 is right)
            let snake_next_dir = 1;
            let food = { x: 0, y: 0 };
            let score = 0;

            // Start the game
            window.onload = function() {
                newGame();
            };

            function newGame() {
                // Reset snake, food, and score
                snake = [{ x: 0, y: 15 }];
                snake_dir = 1;
                snake_next_dir = 1;
                score = 0;
                document.getElementById("score_value").textContent = score;
                addFood();
                mainLoop();
            }

            function mainLoop() {
                moveSnake();
                renderGame();
                setTimeout(mainLoop, 100);
            }

            function moveSnake() {
                let head = snake[0];
                let newHead = {
                    x: head.x + (snake_dir === 1 ? 1 : snake_dir === 3 ? -1 : 0),
                    y: head.y + (snake_dir === 0 ? -1 : snake_dir === 2 ? 1 : 0)
                };

                snake.unshift(newHead);
                snake.pop();

                if (checkCollision(newHead.x, newHead.y, food.x, food.y)) {
                    snake.push({}); // Add length to snake
                    score++;
                    document.getElementById("score_value").textContent = score;
                    addFood();
                }
            }

            function renderGame() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);

                // Draw the snake
                ctx.fillStyle = "#800080";  // Purple snake
                snake.forEach(part => {
                    ctx.fillRect(part.x * BLOCK, part.y * BLOCK, BLOCK, BLOCK);
                });

                // Draw the food (white heart with light blue outline)
                drawHeart(food.x, food.y);
            }

            function addFood() {
                food.x = Math.floor(Math.random() * (canvas.width / BLOCK));
                food.y = Math.floor(Math.random() * (canvas.height / BLOCK));
            }

            function drawHeart(x, y) {
                const centerX = x * BLOCK + BLOCK / 2;
                const centerY = y * BLOCK + BLOCK / 2;
                const size = BLOCK / 2;

                ctx.save();
                ctx.translate(centerX, centerY);

                // Draw the outline (light blue)
                ctx.beginPath();
                ctx.strokeStyle = "#ADD8E6";  // Light blue outline
                ctx.lineWidth = 2;
                ctx.moveTo(0, 0);
                ctx.arc(-size / 2, -size / 4, size / 2, 0, Math.PI, true);
                ctx.arc(size / 2, -size / 4, size / 2, 0, Math.PI, true);
                ctx.lineTo(0, size);
                ctx.stroke();
                ctx.closePath();

                // Draw the heart (white fill)
                ctx.beginPath();
                ctx.fillStyle = "#FFFFFF";  // White fill
                ctx.moveTo(0, 0);
                ctx.arc(-size / 2, -size / 4, size / 2, 0, Math.PI, true);
                ctx.arc(size / 2, -size / 4, size / 2, 0, Math.PI, true);
                ctx.lineTo(0, size);
                ctx.fill();
                ctx.closePath();

                ctx.restore();
            }

            function checkCollision(x1, y1, x2, y2) {
                return x1 === x2 && y1 === y2;
            }

            window.addEventListener("keydown", function(evt) {
                switch (evt.keyCode) {
                    case 37: if (snake_dir !== 1) snake_next_dir = 3; break;  // Left arrow
                    case 38: if (snake_dir !== 2) snake_next_dir = 0; break;  // Up arrow
                    case 39: if (snake_dir !== 3) snake_next_dir = 1; break;  // Right arrow
                    case 40: if (snake_dir !== 0) snake_next_dir = 2; break;  // Down arrow
                }
                snake_dir = snake_next_dir;
            });
        })();
    </script>
</body>
</html>
