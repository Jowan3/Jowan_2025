---
layout: page
title: Snake
description: Snake game
permalink: /snake/
---

{% include nav/home.html %}

✨beginning of my snake page✨
 
<style>
    body {
        background: linear-gradient(to bottom, #ffdbac, #ff7f50);
        overflow: hidden;
        font-family: 'Arial', sans-serif;
    }
    .wrap {
        margin-left: auto;
        margin-right: auto;
    }
    canvas {
        display: none;
        border-style: solid;
        border-width: 10px;
        border-image: linear-gradient(to right, red, green) 1;
        background-color: #fff5e1;
    }
    canvas:focus {
        outline: none;
    }
    /* Menu Styles */
    #menu p, #gameover p, #setting p {
        font-size: 20px;
    }
    #menu a, #gameover a, #setting a {
        font-size: 30px;
        display: block;
    }
    #menu a:hover, #gameover a:hover, #setting a:hover {
        cursor: pointer;
    }
</style>

<h2>Festive Snake Game</h2>
<div class="container">
    <header class="pb-3 mb-4 border-bottom border-primary text-dark">
        <p class="fs-4">Score: <span id="score_value">0</span></p>
    </header>
    <div class="container bg-secondary" style="text-align:center;">
        <div id="menu" class="py-4 text-light">
            <p>Welcome to the Festive Snake Game! Press <span style="background-color: #FFFFFF; color: #000000">Space</span> to begin</p>
            <a id="new_game" class="link-alert">Start Game</a>
        </div>
        <div id="gameover" class="py-4 text-light">
            <p>Game Over! Press <span style="background-color: #FFFFFF; color: #000000">Space</span> to try again.</p>
            <a id="new_game1" class="link-alert">Restart</a>
        </div>
        <canvas id="snake" class="wrap" width="320" height="320" tabindex="1"></canvas>
    </div>
</div>

<script>
(function () {
    const canvas = document.getElementById("snake");
    const ctx = canvas.getContext("2d");
    const BLOCK = 20;
    let snake = [{ x: 8, y: 8 }];
    let direction = { x: 0, y: 0 };
    let food = { x: 5, y: 5 };
    let score = 0;

    function drawBlock(x, y, color) {
        ctx.fillStyle = color;
        ctx.fillRect(x * BLOCK, y * BLOCK, BLOCK, BLOCK);
        ctx.strokeStyle = "#000";
        ctx.strokeRect(x * BLOCK, y * BLOCK, BLOCK, BLOCK);
    }

    function placeFood() {
        food = {
            x: Math.floor(Math.random() * (canvas.width / BLOCK)),
            y: Math.floor(Math.random() * (canvas.height / BLOCK)),
        };
    }

    function update() {
        const head = { x: snake[0].x + direction.x, y: snake[0].y + direction.y };

        if (
            head.x < 0 ||
            head.x >= canvas.width / BLOCK ||
            head.y < 0 ||
            head.y >= canvas.height / BLOCK ||
            snake.some(segment => segment.x === head.x && segment.y === head.y)
        ) {
            document.getElementById("menu").style.display = "none";
            document.getElementById("gameover").style.display = "block";
            return;
        }

        snake.unshift(head);

        if (head.x === food.x && head.y === food.y) {
            score++;
            document.getElementById("score_value").textContent = score;
            placeFood();
        } else {
            snake.pop();
        }

        draw();
        setTimeout(update, 200 - Math.min(score * 5, 150));
    }

    function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        snake.forEach((segment, index) => {
            drawBlock(segment.x, segment.y, index === 0 ? "#d2691e" : "#f4a460");
        });
        drawBlock(food.x, food.y, "#ff0000");
    }

    function startGame() {
        score = 0;
        snake = [{ x: 8, y: 8 }];
        direction = { x: 0, y: 0 };
        placeFood();
        document.getElementById("menu").style.display = "none";
        document.getElementById("gameover").style.display = "none";
        canvas.style.display = "block";
        canvas.focus();
        update();
    }

    function changeDirection(event) {
        const { key } = event;
        if (key === "ArrowUp" && direction.y === 0) direction = { x: 0, y: -1 };
        if (key === "ArrowDown" && direction.y === 0) direction = { x: 0, y: 1 };
        if (key === "ArrowLeft" && direction.x === 0) direction = { x: -1, y: 0 };
        if (key === "ArrowRight" && direction.x === 0) direction = { x: 1, y: 0 };
    }

    window.addEventListener("keydown", changeDirection);
    window.addEventListener("keydown", e => {
        if (e.code === "Space" && canvas.style.display !== "block") startGame();
        if (["ArrowUp", "ArrowDown", "ArrowLeft", "ArrowRight"].includes(e.key)) e.preventDefault();
    });

    document.getElementById("new_game").addEventListener("click", startGame);
    document.getElementById("new_game1").addEventListener("click", startGame);
})();
</script>
