---
layout: page
title: leaderboard
description: leaderbaord
permalink: /leaderboard/
---

{% include nav/home.html %}

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chess Leaderboard</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: rgba(0, 0, 0, 0.8);
            color: #fff;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .leaderboard-container {
            width: 90%;
            max-width: 600px;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.6);
        }

        .leaderboard-title {
            font-size: 28px;
            font-weight: bold;
            text-align: center;
            margin-bottom: 20px;
            text-transform: uppercase;
        }

        .leaderboard {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .player-entry {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .player-rank {
            font-size: 20px;
            font-weight: bold;
            width: 40px;
            text-align: center;
        }

        .player-details {
            display: flex;
            flex-direction: column;
            gap: 5px;
            width: 100%;
        }

        .player-name {
            font-size: 16px;
            font-weight: bold;
            color: #fff;
        }

        .player-wins {
            font-size: 14px;
            color: rgba(255, 255, 255, 0.8);
        }

        .bar-container {
            background: rgba(255, 255, 255, 0.2);
            height: 20px;
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .bar {
            height: 100%;
            background: linear-gradient(90deg, #FFD700, #FFA500);
            width: 0%;
            border-radius: 10px;
        }

        .player-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: 2px solid white;
            object-fit: cover;
        }

        .note {
            font-size: 14px;
            text-align: center;
            margin-top: 15px;
            opacity: 0.8;
        }
    </style>
</head>
<body>
    <div class="leaderboard-container">
        <div class="leaderboard-title">Weekly Chess Leaderboard</div>
        <div class="leaderboard">
            <!-- Player 1 -->
            <div class="player-entry">
                <div class="player-rank">1</div>
                <img src="https://via.placeholder.com/50" alt="Player 1" class="player-avatar">
                <div class="player-details">
                    <div class="player-name">Player 1</div>
                    <div class="player-wins">20 Wins</div>
                    <div class="bar-container">
                        <div class="bar" style="width: 100%;"></div>
                    </div>
                </div>
            </div>
            <!-- Player 2 -->
            <div class="player-entry">
                <div class="player-rank">2</div>
                <img src="https://via.placeholder.com/50" alt="Player 2" class="player-avatar">
                <div class="player-details">
                    <div class="player-name">Player 2</div>
                    <div class="player-wins">15 Wins</div>
                    <div class="bar-container">
                        <div class="bar" style="width: 75%;"></div>
                    </div>
                </div>
            </div>
            <!-- Player 3 -->
            <div class="player-entry">
                <div class="player-rank">3</div>
                <img src="https://via.placeholder.com/50" alt="Player 3" class="player-avatar">
                <div class="player-details">
                    <div class="player-name">Player 3</div>
                    <div class="player-wins">10 Wins</div>
                    <div class="bar-container">
                        <div class="bar" style="width: 50%;"></div>
                    </div>
                </div>
            </div>
        </div>
        <div class="note">* Weekly leaderboard resets every Monday at midnight.</div>
    </div>
</body>
</html>
