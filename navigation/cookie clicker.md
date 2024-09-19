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
    <title>Cookie Clicker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #ffffff; /* White background */
        }
        #cookie {
            width: 200px;
            height: 200px;
            background-image: url('https://img.icons8.com/ios/200/000000/cookie.png'); /* Realistic cookie image */
            background-size: cover;
            border: none;
            border-radius: 50%;
            margin: 0 auto;
            cursor: pointer;
            box-shadow: 0 0 10px #888;
        }
        #counter {
            font-size: 2em;
            margin: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 1em;
            margin: 10px;
        }
    </style>
</head>
<body>

    <h1>Cookie Clicker Game</h1>
    <div id="cookie" onclick="addCookie()"></div>
    <div id="counter">Cookies: 0</div>
    <button onclick="buyCursor()">Buy Cursor (Cost: 10 cookies)</button>
    <div id="cursors">Cursors: 0</div>

    <audio id="biteSound" src="https://www.soundjay.com/button/sounds/button-3.mp3"></audio> <!-- Bite sound -->

    <script>
        let cookies = 0;
        let cursors = 0;

        function updateCounter() {
            document.getElementById("counter").innerText = `Cookies: ${cookies}`;
            document.getElementById("cursors").innerText = `Cursors: ${cursors}`;
        }

        function addCookie() {
            cookies++;
            updateCounter();
            playBiteSound(); // Play bite sound when clicking the cookie
        }

        function buyCursor() {
            const cursorCost = 10;
            if (cookies >= cursorCost) {
                cookies -= cursorCost;
                cursors++;
                updateCounter();
                startAutoClick();
            } else {
                alert("Not enough cookies!");
            }
        }

        function startAutoClick() {
            setInterval(() => {
                cookies += cursors;
                updateCounter();
            }, 1000);
        }

        function playBiteSound() {
            const biteSound = document.getElementById("biteSound");
            biteSound.currentTime = 0; // Reset sound
            biteSound.play(); // Play bite sound
        }
    </script>

</body>
</html>
