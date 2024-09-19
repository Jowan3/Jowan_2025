---
layout: page
title: Cookie Clicker
description: cookie clicker game
permalink: /cookie clicker/
---

{% include nav/home.html %}


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cute Purple Cookie Clicker</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0e5f5;
            font-family: 'Arial', sans-serif;
        }

        h1 {
            color: #9b59b6;
        }

        .cookie {
            background-image: url('https://img.icons8.com/ios/100/9b59b6/cookie.png'); /* Cookie image */
            background-size: cover;
            width: 100px;
            height: 100px;
            border: none;
            cursor: pointer;
            transition: transform 0.1s;
        }

        .cookie:hover {
            transform: scale(1.1);
        }

        .score {
            margin-top: 20px;
            font-size: 24px;
            color: #9b59b6;
        }
    </style>
</head>
<body>
    <h1>Cute Purple Cookie Clicker</h1>
    <button class="cookie" id="cookieButton"></button>
    <div class="score">Cookies: <span id="cookieCount">0</span></div>
    
    <audio id="munchSound" src="https://www.soundjay.com/button/sounds/button-3.mp3"></audio> <!-- Munching sound -->

    <script>
        let cookieCount = 0;
        const cookieCountDisplay = document.getElementById('cookieCount');
        const cookieButton = document.getElementById('cookieButton');
        const munchSound = document.getElementById('munchSound');

        cookieButton.addEventListener('click', () => {
            cookieCount++;
            cookieCountDisplay.innerText = cookieCount;
            munchSound.currentTime = 0; // Reset sound
            munchSound.play(); // Play munching sound
        });
    </script>
</body>
</html>
