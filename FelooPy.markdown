---
layout: page
title: 📦FelooPy
permalink: /feloopy/
---

<p align="center">
  <img title="FelooPy Library in Python" alt="FelooPy Library in Python" src="https://github.com/ktafakkori/feloopy/blob/main/miscellaneous/logo/logo1.png">
</p>

[![GitHub release](https://img.shields.io/badge/version-0.2.6-orange.svg)](https://github.com/ktafakkori/feloopy/releases)
[![Python 3.10](https://img.shields.io/badge/python-3.10-blue.svg)](https://www.python.org/downloads/release/python-310/)
![Package Size](https://img.shields.io/github/languages/code-size/ktafakkori/feloopy)
![Supporters](https://img.shields.io/github/stars/ktafakkori/feloopy)
![Downloads](https://img.shields.io/pypi/dm/feloopy.svg)
[![Total Downloads](https://static.pepy.tech/personalized-badge/feloopy?period=total&units=international_system&left_color=grey&right_color=blue&left_text=downloads)](https://pepy.tech/project/feloopy)
![Release Date](https://img.shields.io/github/release-date/ktafakkori/feloopy.svg)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/ktafakkori/feloopy.svg)](http://isitmaintained.com/project/ktafakkori/feloopy "Average time to resolve an issue")
[![Percentage of issues still open](http://isitmaintained.com/badge/open/ktafakkori/feloopy.svg)](http://isitmaintained.com/project/ktafakkori/feloopy "Percentage of issues still open")
![GitHub contributors](https://img.shields.io/github/contributors/ktafakkori/feloopy.svg)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

# FelooPy: An integrated optimization environment for AutoOR in Python


<html>

<head>
    <title>Snake Game</title>
    <style>
        body { background: #000; color: #fff; }
        #gameCanvas { background: transparent; }
    </style>
</head>

<body>
    <canvas id="gameCanvas" width="800" height="600"></canvas>
    <script>
        var canvas = document.getElementById('gameCanvas');
        var context = canvas.getContext('2d');

        var snake, prey, direction, updateInterval, drawInterval, gameOver;

        function startGame() {
            snake = [{ top: canvas.height / 2, left: canvas.width / 2, direction: 'right' }];
            prey = generatePrey();
            direction = 'right';
            gameOver = false;

            if (updateInterval) clearInterval(updateInterval);
            if (drawInterval) clearInterval(drawInterval);

            updateInterval = setInterval(update, 100);
            drawInterval = setInterval(draw, 100);
        }

        function generatePrey() {
            return {
                top: Math.floor(Math.random() * (canvas.height / 20)) * 20,
                left: Math.floor(Math.random() * (canvas.width / 20)) * 20
            };
        }

        function draw() {
            if (gameOver) {
                startGame();
                return;
            }

            context.clearRect(0, 0, canvas.width, canvas.height);

            context.fillStyle = 'lightblue';
            for (var i = 0; i < snake.length; i++) {
                var segment = snake[i];
                context.fillRect(segment.left, segment.top, 40, 40);
            }

            if (prey !== null) {
                context.fillStyle = 'orange';
                context.fillRect(prey.left, prey.top, 40, 40);
            }
        }

        function update() {
            if (gameOver || prey === null) return;

            var head = Object.assign({}, snake[0]);

            if (prey.top < head.top) {
                direction = 'up';
            } else if (prey.top > head.top) {
                direction = 'down';
            } else if (prey.left < head.left) {
                direction = 'left';
            } else if (prey.left > head.left) {
                direction = 'right';
            }

            if (direction === 'left') {
                head.left -= 20;
            } else if (direction === 'right') {
                head.left += 20;
            } else if (direction === 'up') {
                head.top -= 20;
            } else if (direction === 'down') {
                head.top += 20;
            }

            snake.unshift(head);

            if (head.left === prey.left && head.top === prey.top) {
                snake.push({});
                prey = generatePrey();
            } else {
                snake.pop();
            }
        }

        startGame();
    </script>
</body>
</html>



<!--#comment
<div class="feloopy-options">

  <div class="feloopy-option">
    <h3>Free</h3>
    <ul>
      <li>Feature 1</li>
      <li>Feature 2</li>
  
    </ul>
    <a href="" class="btn">Select</a>
  </div>

  <div class="feloopy-option">
    <h3>Extensions</h3>
    <ul>
      <li>Feature 1</li>
      <li>Feature 2</li>

    </ul>
    <a href="" class="btn">Select</a>
  </div>

  <div class="feloopy-option">
    <h3>Premium</h3>
    <ul>
      <li>Feature 1</li>
      <li>Feature 2</li>

    </ul>
    <a href="" class="btn">Select</a>
  </div>
</div> 
#-->