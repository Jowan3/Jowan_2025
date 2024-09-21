---
layout: page 
title: kitties
permalink: /kittes/
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pat the Cat</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f8ff;
            flex-direction: column;
        }
        img {
            width: 300px; /* Adjust the size of the cat image */
            cursor: pointer;
        }
        #message {
            margin-top: 20px;
            font-size: 24px;
            color: #333;
        }
    </style>
</head>
<body>

    <img src="https://placekitten.com/300/300" alt="Cute Cat" id="cat">
    <div id="message"></div>

    <script>
        const cat = document.getElementById('cat');
        const messageDiv = document.getElementById('message');

        cat.addEventListener('click', () => {
            messageDiv.textContent = "You patted the cat! 😺";
        });
    </script>

</body>
</html>
