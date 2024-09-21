---
layout: page
title: Emoji Game
description: Guess the movie by the emoji
permalink: /emoji game/
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Guess the Movie from Emojis</title>
    <link href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@300&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Comfortaa', sans-serif;
            background-color: #f5f5f5;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            text-align: center;
        }

        .game-container {
            background-color: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }

        .emojis {
            font-size: 2.5rem;
            margin: 20px 0;
        }

        input[type="text"] {
            padding: 10px;
            font-size: 16px;
            border: 2px solid #9b59b6;
            border-radius: 5px;
            width: 100%;
            margin-bottom: 10px;
        }

        button {
            font-family: 'Comfortaa', sans-serif;
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

        .result {
            font-size: 1.2rem;
            color: #27ae60;
        }

        .wrong {
            color: #e74c3c;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <h1>Guess the Movie</h1>
        <div class="emojis" id="emojiDisplay">🎥❓</div>
        <input type="text" id="guessInput" placeholder="Enter movie name..." />
        <button onclick="checkGuess()">Submit Guess</button>
        <div id="resultMessage" class="result"></div>
        <button id="nextButton" onclick="nextMovie()" style="display: none;">Next Movie</button>
    </div>

    <script>
        const movies = [
            { emojis: '🦁👑', name: 'Lion King' },
            { emojis: '🧑‍🚀🚀🌕', name: 'Apollo 13' },
            { emojis: '🦈🌊', name: 'Jaws' },
            { emojis: '👸❄️', name: 'Frozen' },
            { emojis: '🧙‍♂️🧹⚡', name: 'Harry Potter' },
            { emojis: '🤖👦', name: 'Terminator' }
        ];

        let currentMovieIndex = 0;

        function displayMovie() {
            const emojiDisplay = document.getElementById('emojiDisplay');
            emojiDisplay.innerText = movies[currentMovieIndex].emojis;
        }

        function checkGuess() {
            const guessInput = document.getElementById('guessInput').value.trim().toLowerCase();
            const resultMessage = document.getElementById('resultMessage');
            const movieName = movies[currentMovieIndex].name.toLowerCase();

            if (guessInput === movieName) {
                resultMessage.textContent = 'Correct! 🎉';
                resultMessage.classList.remove('wrong');
                document.getElementById('nextButton').style.display = 'block';
            } else {
                resultMessage.textContent = 'Wrong guess, try again! 😢';
                resultMessage.classList.add('wrong');
            }
        }

        function nextMovie() {
            currentMovieIndex = (currentMovieIndex + 1) % movies.length;
            displayMovie();
            document.getElementById('guessInput').value = '';
            document.getElementById('resultMessage').textContent = '';
            document.getElementById('nextButton').style.display = 'none';
        }

        // Initialize the game
        displayMovie();
    </script>
</body>
</html>
