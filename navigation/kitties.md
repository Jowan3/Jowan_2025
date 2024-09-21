---
layout: page 
title: kitties
permalink: /kittes/
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cutest Cats Carousel</title>
    <style>
        * {
            box-sizing: border-box;
        }
        
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f5f5f5;
        }

        .carousel {
            position: relative;
            max-width: 600px;
            max-height: 400px;
            overflow: hidden;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .carousel img {
            width: 100%;
            height: 100%;
            display: none;
        }

        .carousel img.active {
            display: block;
        }

        .prev, .next {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(0, 0, 0, 0.5);
            color: white;
            padding: 10px;
            border: none;
            cursor: pointer;
            font-size: 18px;
            border-radius: 50%;
        }

        .prev {
            left: 10px;
        }

        .next {
            right: 10px;
        }

        .dots {
            text-align: center;
            position: absolute;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
        }

        .dot {
            cursor: pointer;
            height: 10px;
            width: 10px;
            margin: 0 5px;
            background-color: #bbb;
            border-radius: 50%;
            display: inline-block;
        }

        .dot.active {
            background-color: #717171;
        }

    </style>
</head>
<body>

<div class="carousel">
    <img src="https://placekitten.com/600/400" class="active" alt="Cute Cat 1">
    <img src="https://placekitten.com/601/400" alt="Cute Cat 2">
    <img src="https://placekitten.com/602/400" alt="Cute Cat 3">
    <img src="https://placekitten.com/603/400" alt="Cute Cat 4">
    <img src="https://placekitten.com/604/400" alt="Cute Cat 5">
    <img src="https://placekitten.com/605/400" alt="Cute Cat 6">
    <img src="https://placekitten.com/606/400" alt="Cute Cat 7">

    <button class="prev" onclick="changeSlide(-1)">&#10094;</button>
    <button class="next" onclick="changeSlide(1)">&#10095;</button>

    <div class="dots">
        <span class="dot active" onclick="currentSlide(1)"></span>
        <span class="dot" onclick="currentSlide(2)"></span>
        <span class="dot" onclick="currentSlide(3)"></span>
        <span class="dot" onclick="currentSlide(4)"></span>
        <span class="dot" onclick="currentSlide(5)"></span>
        <span class="dot" onclick="currentSlide(6)"></span>
        <span class="dot" onclick="currentSlide(7)"></span>
    </div>
</div>

<script>
    let slideIndex = 1;
    showSlides(slideIndex);

    function changeSlide(n) {
        showSlides(slideIndex += n);
    }

    function currentSlide(n) {
        showSlides(slideIndex = n);
    }

    function showSlides(n) {
        let slides = document.querySelectorAll('.carousel img');
        let dots = document.querySelectorAll('.dot');
        
        if (n > slides.length) {slideIndex = 1}    
        if (n < 1) {slideIndex = slides.length}
        
        slides.forEach(slide => slide.style.display = 'none');
        dots.forEach(dot => dot.classList.remove('active'));
        
        slides[slideIndex-1].style.display = 'block';  
        dots[slideIndex-1].classList.add('active');
    }

    // Optional: Auto slide every 5 seconds
    setInterval(function() {
        changeSlide(1);
    }, 5000);
</script>

</body>
</html>