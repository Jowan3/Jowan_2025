---
layout: page
title: Snake
description: Snake game
permalink: /snake/
---

{% include nav/home.html %}

✨beginning of my snake page✨
 
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cute Purple Snake Game - 8-Bit</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="game-container">
        <canvas id="gameCanvas" width="400" height="400"></canvas>
        <div class="score">Score: <span id="score">0</span></div>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0e5f5;
    font-family: 'Press Start 2P', cursive; /* 8-bit font */
}

.game-container {
    border: 5px solid #9b59b6;
    border-radius: 10px;
    padding: 10px;
    background-color: #ffffff;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
}

canvas {
    background-color: #e0d6e8;
    image-rendering: pixelated; /* Ensure pixelated style */
}

.score {
    text-align: center;
    font-size: 24px;
    margin-top: 10px;
    color: #9b59b6;
}
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");
const box = 20;
let snake = [{ x: box * 5, y: box * 5 }];
let direction = { x: 0, y: 0 };
let fruit = { x: Math.floor(Math.random() * 20) * box, y: Math.floor(Math.random() * 20) * box };
let score = 0;

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

    // Draw the fruit (heart)
    const heartImg = new Image();
    heartImg.src = 'https://img.icons8.com/ios/50/ffffff/heart.png'; // Heart image URL
    heartImg.onload = function () {
        ctx.drawImage(heartImg, fruit.x, fruit.y, box, box);
    }

    // Move the snake
    const head = { x: snake[0].x + direction.x * box, y: snake[0].y + direction.y * box };
    
    if (head.x === fruit.x && head.y === fruit.y) {
        score++;
        document.getElementById("score").innerText = score;
        fruit = { x: Math.floor(Math.random() * 20) * box, y: Math.floor(Math.random() * 20) * box };
    } else {
        snake.pop();
    }

    snake.unshift(head);

    // Game over conditions
    if (head.x < 0 || head.x >= canvas.width || head.y < 0 || head.y >= canvas.height || collision(head, snake)) {
        clearInterval(game);
        alert("Game Over! Your score: " + score);
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

const game = setInterval(draw, 100);
