---
layout: page
title: Cute Cats
description: the cutest cats
permalink: /cute-cats/
---

{% include nav/home.html %}

<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Cute Cats Gallery</title>
   <style>
       body {
           display: flex;
           flex-wrap: wrap;
           justify-content: center;
           align-items: center;
           background-color: #f5f5f5;
           font-family: Arial, sans-serif;
       }
       .cat {
           margin: 10px;
           border: 2px solid #9b59b6;
           border-radius: 10px;
           overflow: hidden;
           box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
       }
       .cat img {
           width: 200px;
           height: auto;
           border-bottom: 2px solid #9b59b6;
       }
       .cat-title {
           text-align: center;
           padding: 10px;
           background-color: #fff;
       }
   </style>
</head>
<body>

   <div class="cat">
       <img src="https://placekitten.com/200/300" alt="Cute Cat 1">
       <div class="cat-title">Cute Cat 1</div>
   </div>

   <div class="cat">
       <img src="https://placekitten.com/201/300" alt="Cute Cat 2">
       <div class="cat-title">Cute Cat 2</div>
   </div>

   <div class="cat">
       <img src="https://placekitten.com/202/300" alt="Cute Cat 3">
       <div class="cat-title">Cute Cat 3</div>
   </div>

   <div class="cat">
       <img src="https://placekitten.com/203/300" alt="Cute Cat 4">
       <div class="cat-title">Cute Cat 4</div>
   </div>

   <div class="cat">
       <img src="https://placekitten.com/204/300" alt="Cute Cat 5">
       <div class="cat-title">Cute Cat 5</div>
   </div>

</body>
</html>
