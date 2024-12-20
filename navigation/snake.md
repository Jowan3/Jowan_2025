---
layout: page
title: Snake
description: Snake game
permalink: /snake/
---

{% include nav/home.html %}

✨beginning of my snake page✨
 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Festive Snake Game</title>
    <style>
        body {
            margin: 0;
            overflow-x: hidden;
        }

        .wrap {
            margin-left: auto;
            margin-right: auto;
        }

        canvas {
            border-style: solid;
            border-width: 10px;
            border-color: #FF6347;
            background: #FFFACD url('https://example.com/festive-background.jpg') no-repeat center;
            background-size: cover;
        }

        canvas:focus {
            outline: none;
        }

        h2 {
            text-align: center;
            color: #FF6347;
            font-family: 'Comic Sans MS', cursive, sans-serif;
        }

        header {
            text-align: center;
        }

        #gameover p, #setting p, #menu p {
            font-size: 20px;
            color: #333;
        }

        #gameover a, #setting a, #menu a {
            font-size: 30px;
            display: block;
            text-decoration: none;
            color: #FF6347;
        }

        #gameover a:hover, #setting a:hover, #menu a:hover {
            cursor: pointer;
            text-decoration: underline;
        }

        #menu {
            display: block;
        }

        #gameover {
            display: none;
        }

        #setting {
            display: none;
        }

        #setting input {
            display: none;
        }

        #setting label {
            cursor: pointer;
        }

        #setting input:checked + label {
            background-color: #FFF;
            color: #000;
        }
    </style>
</head>
<body>
    <h2>Festive Snake Game</h2>
    <div class="container">
        <header class="pb-3 mb-4 border-bottom border-primary text-dark">
            <p class="fs-4">Score: <span id="score_value">0</span></p>
        </header>
        <div class="container bg-secondary" style="text-align:center;">
            <!-- Main Menu -->
            <div id="menu" class="py-4 text-light">
                <p>Welcome to Festive Snake, press <span style="background-color: #FFFFFF; color: #000000">space</span> to begin</p>
                <a id="new_game" class="link-alert">new game</a>
                <a id="setting_menu" class="link-alert">settings</a>
            </div>
            <!-- Game Over -->
            <div id="gameover" class="py-4 text-light">
                <p>Game Over, press <span style="background-color: #FFFFFF; color: #000000">space</span> to try again</p>
                <a id="new_game1" class="link-alert">new game</a>
                <a id="setting_menu1" class="link-alert">settings</a>
            </div>
            <!-- Play Screen -->
            <canvas id="snake" class="wrap" width="320" height="320" tabindex="1"></canvas>
            <!-- Settings Screen -->
            <div id="setting" class="py-4 text-light">
                <p>Settings Screen, press <span style="background-color: #FFFFFF; color: #000000">space</span> to go back to playing</p>
                <a id="new_game2" class="link-alert">new game</a>
                <br>
                <p>Speed:
                    <input id="speed1" type="radio" name="speed" value="120" checked/>
                    <label for="speed1">Slow</label>
                    <input id="speed2" type="radio" name="speed" value="75"/>
                    <label for="speed2">Normal</label>
                    <input id="speed3" type="radio" name="speed" value="35"/>
                    <label for="speed3">Fast</label>
                </p>
                <p>Wall:
                    <input id="wallon" type="radio" name="wall" value="1" checked/>
                    <label for="wallon">On</label>
                    <input id="walloff" type="radio" name="wall" value="0"/>
                    <label for="walloff">Off</label>
                </p>
            </div>
        </div>
    </div>

    <script>
        (function () {
            const canvas = document.getElementById("snake");
            const ctx = canvas.getContext("2d");
            const BLOCK = 10;

            let SCREEN = -1; // Start at menu
            let snake;
            let snake_dir;
            let snake_next_dir;
            let snake_speed;
            let food = { x: 0, y: 0 };
            let score;
            let wall;

            const ele_score = document.getElementById("score_value");
            const speed_setting = document.getElementsByName("speed");
            const wall_setting = document.getElementsByName("wall");
            const screen_menu = document.getElementById("menu");
            const screen_game_over = document.getElementById("gameover");
            const screen_snake = document.getElementById("snake");
            const screen_setting = document.getElementById("setting");

            const showScreen = function (screen_opt) {
                SCREEN = screen_opt;
                screen_menu.style.display = screen_opt === -1 ? "block" : "none";
                screen_game_over.style.display = screen_opt === 1 ? "block" : "none";
                screen_snake.style.display = screen_opt === 0 ? "block" : "none";
                screen_setting.style.display = screen_opt === 2 ? "block" : "none";
            };

            window.onload = function () {
                document.getElementById("new_game").onclick = newGame;
                document.getElementById("new_game1").onclick = newGame;
                document.getElementById("new_game2").onclick = newGame;
                document.getElementById("setting_menu").onclick = function () {
                    showScreen(2);
                };
                document.getElementById("setting_menu1").onclick = function () {
                    showScreen(2);
                };
                setSnakeSpeed(150);
                speed_setting.forEach((radio) => {
                    radio.onclick = function () {
                        setSnakeSpeed(this.value);
                    };
                });

                setWall(1);
                wall_setting.forEach((radio) => {
                    radio.onclick = function () {
                        setWall(this.value);
                    };
                });

                window.addEventListener("keydown", function (evt) {
                    if (evt.code === "Space" && SCREEN !== 0) newGame();
                });

                canvas.addEventListener("keydown", function (evt) {
                    changeDir(evt.keyCode);
                });
            };

            const newGame = function () {
                showScreen(0);
                screen_snake.focus();
                score = 0;
                ele_score.innerHTML = "0";
                snake = [{ x: 10, y: 15 }];
                snake_dir = 1;
                snake_next_dir = 1;
                addFood();
                mainLoop();
            };

            const mainLoop = function () {
                // Game logic...
            };

            const changeDir = function (key) {
                // Handle direction changes
            };

            const setSnakeSpeed = function (speed_value) {
                snake_speed = speed_value;
            };

            const setWall = function (wall_value) {
                wall = parseInt(wall_value);
            };

            const addFood = function () {
                food.x = Math.floor(Math.random() * (canvas.width / BLOCK));
                food.y = Math.floor(Math.random() * (canvas.height / BLOCK));
            };
        })();
    </script>
</body>
</html>
