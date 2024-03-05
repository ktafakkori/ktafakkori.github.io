

# 

## **FelooPy**
_An integrated optimization environment for automated operations research in Python_

- Explore the project on [GitHub](https://github.com/ktafakkori/feloopy).
- Consult the [Documentation](https://feloopy.readthedocs.io/en/latest/) for more details.
- Visit the [PyPI](https://pypi.org/project/feloopy/) page to learn about the project host.
- Download and install the latest version from [Releases](https://github.com/ktafakkori/feloopy/releases/latest).

[![GitHub stars](https://img.shields.io/github/stars/ktafakkori/feloopy?label=stars&style=flat-rounded&color=success&logo=github)](https://github.com/ktafakkori/feloopy/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/ktafakkori/feloopy?label=forks&style=flat-rounded&color=blue)](https://github.com/ktafakkori/feloopy/network/members)
[![GitHub tag](https://img.shields.io/github/v/tag/ktafakkori/feloopy?sort=semver&label=version&style=flat-rounded&color=orange)](https://github.com/ktafakkori/feloopy/releases)
[![Downloads](https://pepy.tech/badge/feloopy?style=flat-rounded&color=green)](https://pepy.tech/project/feloopy)
[![GitHub](https://img.shields.io/github/license/ktafakkori/feloopy?style=flat-rounded&color=red)](https://github.com/ktafakkori/feloopy/blob/main/LICENSE)

<table align="center">
  <tr>
    <td style="text-align: center;">
      <canvas id="gameCanvas" width="400" height="400" style="border: 3px solid white;"></canvas>
    </td>
  </tr>
</table>

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
          context.save();
          context.translate(segment.left + 20, segment.top + 20);
          context.rotate((segment.direction === 'right' ? 45 : segment.direction === 'down' ? 135 : segment.direction === 'left' ? 225 : 315) * Math.PI / 180);

          context.fillRect(-20, -20, 40, 40);

          if (i === 0) {
              context.fillStyle = 'white';
              context.beginPath();
              context.arc(0, -10, 6, 0, Math.PI * 2);
              context.closePath();
              context.fill();
          }

          context.restore();
      }

      if (prey !== null) {
          context.fillStyle = 'orange';
          context.save();
          context.translate(prey.left + 20, prey.top + 20);
          context.rotate(45 * Math.PI / 180);
          context.fillRect(-20, -20, 40, 40);

          context.fillStyle = 'white';
          context.beginPath();
          context.arc(0, -10, 6, 0, Math.PI * 2);
          context.closePath();
          context.fill();

          context.restore();
      }
  }

  function update() {
      if (gameOver || prey === null) return;

      var head = Object.assign({}, snake[0]);
      var preyDirection;

      if (prey.top < head.top) {
          direction = 'up';
          preyDirection = 'down';
      } else if (prey.top > head.top) {
          direction = 'down';
          preyDirection = 'up';
      } else if (prey.left < head.left) {
          direction = 'left';
          preyDirection = 'right';
      } else if (prey.left > head.left) {
          direction = 'right';
          preyDirection = 'left';
      }

      head.direction = direction;

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