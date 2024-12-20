---
layout: page
title: leaderboard
description: leaderbaord
permalink: /leaderboard/
---

{% include nav/home.html %}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chess Leaderboard</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            color: #fff;
        }

        .leaderboard-container {
            width: 80%;
            max-width: 800px;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.6);
            text-align: center;
        }

        .leaderboard-title {
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 20px;
            text-transform: uppercase;
        }

        .podium {
            display: flex;
            align-items: flex-end;
            justify-content: center;
            gap: 20px;
            position: relative;
        }

        .podium-stand {
            width: 150px;
            text-align: center;
            border-radius: 10px 10px 0 0;
            position: relative;
        }

        .podium-1 {
            background: gold;
            height: 200px;
        }

        .podium-2 {
            background: silver;
            height: 160px;
        }

        .podium-3 {
            background: #cd7f32;
            height: 130px;
        }

        .player {
            position: absolute;
            top: -80px;
            left: 50%;
            transform: translateX(-50%);
            text-align: center;
        }

        .player img {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            border: 3px solid white;
            margin-bottom: 8px;
        }

        .player-name {
            font-weight: bold;
            font-size: 16px;
        }

        .player-wins {
            font-size: 14px;
        }

        .note {
            font-size: 14px;
            margin-top: 15px;
            opacity: 0.8;
        }
    </style>
</head>
<body>
    <div class="leaderboard-container">
        <div class="leaderboard-title">Weekly Chess Leaderboard</div>
        <div class="podium">
            <!-- 2nd Place -->
            <div class="podium-stand podium-2">
                <div class="player">
                    <img src="https://via.placeholder.com/70" alt="Player 2">
                    <div class="player-name">Player 2</div>
                    <div class="player-wins">15 Wins</div>
                </div>
                2nd
            </div>
            <!-- 1st Place -->
            <div class="podium-stand podium-1">
                <div class="player">
                    <img src="https://via.placeholder.com/70" alt="Player 1">
                    <div class="player-name">Player 1</div>
                    <div class="player-wins">20 Wins</div>
                </div>
                1st
            </div>
            <!-- 3rd Place -->
            <div class="podium-stand podium-3">
                <div class="player">
                    <img src="https://via.placeholder.com/70" alt="Player 3">
                    <div class="player-name">Player 3</div>
                    <div class="player-wins">10 Wins</div>
                </div>
                3rd
            </div>
        </div>
        <div class="note">* Weekly leaderboard resets every Monday at midnight.</div>
    </div>
</body>
</html>
