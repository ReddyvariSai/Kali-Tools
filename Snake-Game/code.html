```bash

const gridSize = 20;
const tileCount = 30;
const MIN_SPEED = 40; // Minimum speed limit in ms
let snake, direction, food, score, speed, gameLoop, isGameOver;
let highScore = Number(localStorage.getItem('snakeHighScore') || 0);

// --- Coin and Snake Color Shop Logic ---
let goldCoins = Number(localStorage.getItem('snakeGoldCoins') || 0);
let silverCoins = Number(localStorage.getItem('snakeSilverCoins') || 0);
let unlockedColors = JSON.parse(localStorage.getItem('snakeColors') || '["#111"]');
let selectedColor = unlockedColors[0];
const snakeColorOptions = [
  {color: '#111', name: 'Black', cost: {gold: 0, silver: 0}},
  {color: '#2e86de', name: 'Blue', cost: {gold: 2, silver: 10}},
  {color: '#e17055', name: 'Orange', cost: {gold: 1, silver: 8}},
  {color: '#00b894', name: 'Green', cost: {gold: 2, silver: 12}},
  {color: '#fdcb6e', name: 'Yellow', cost: {gold: 3, silver: 15}},
  {color: '#d35400', name: 'Brown', cost: {gold: 1, silver: 5}},
  {color: '#6c3483', name: 'Purple', cost: {gold: 4, silver: 20}}
];
let birdsEaten = 0;

// Add coin display to UI
let coinBar = document.createElement('div');
coinBar.id = 'coinBar';
coinBar.style = 'color:#ffe66d;font-size:1.1em;margin-bottom:10px;';
coinBar.innerHTML = `
  <span style="color:gold;">&#x1F7E1; Gold: <span id="goldCoinCount">${goldCoins}</span></span>
  <span style="color:silver;margin-left:20px;">&#x26AA; Silver: <span id="silverCoinCount">${silverCoins}</span></span>
`;
document.body.insertBefore(coinBar, document.body.children[1]);

function updateCoinBar() {
  document.getElementById('goldCoinCount').textContent = goldCoins;
  document.getElementById('silverCoinCount').textContent = silverCoins;
}

// --- Shop UI ---
function showShop() {
  let shop = document.createElement('div');
  shop.id = 'shopScreen';
  shop.style = `position:fixed;z-index:20;top:0;left:0;width:100vw;height:100vh;background:#111d;display:flex;flex-direction:column;align-items:center;justify-content:center;`;
  shop.innerHTML = `<div style='color:#ffe66d;font-size:2em;margin-bottom:20px;'>Snake Shop</div>
    <div style='display:flex;gap:18px;flex-wrap:wrap;justify-content:center;'>
      ${snakeColorOptions.map(opt => `
        <div style='display:flex;flex-direction:column;align-items:center;'>
          <canvas width='38' height='38' style='border-radius:50%;background:#222;box-shadow:0 2px 8px #000;margin-bottom:6px;display:block;' id='snakeImg_${opt.color.replace("#","")}'></canvas>
          <canvas width='38' height='38' style='border-radius:50%;background:#222;box-shadow:0 2px 8px #000;margin-bottom:6px;display:block;' id='birdImg_${opt.color.replace("#","")}'></canvas>
          <div style='color:#fff;font-size:1em;'>${opt.name}</div>
          <button style='margin-top:4px;font-size:1em;padding:4px 12px;' ${unlockedColors.includes(opt.color)?'disabled':''} onclick='buySnakeColor("${opt.color}")'>
            ${unlockedColors.includes(opt.color)?'Owned':`Buy (${opt.cost.gold}&#x1F7E1; ${opt.cost.silver}&#x26AA;)`}
          </button>
          <button style='margin-top:2px;font-size:0.9em;padding:2px 10px;' ${unlockedColors.includes(opt.color)?'':'disabled'} onclick='selectSnakeColor("${opt.color}")'>
            ${selectedColor===opt.color?'Selected':'Select'}
          </button>
        </div>
      `).join('')}
    </div>
    <button style='margin-top:30px;font-size:1.2em;padding:10px 30px;' onclick='closeShop()'>Close</button>
  `;
  document.body.appendChild(shop);
  // Bird color options for shop preview
  const birdShopColors = ['#fff', '#e53935', '#1976d2', '#43ea5e', '#fdcb6e', '#a3e4f7', '#f7b731'];
  // Draw mini snake and bird images for each color
  snakeColorOptions.forEach((opt, idx) => {
    // Draw snake (top)
    let c = document.getElementById('snakeImg_' + opt.color.replace('#',''));
    if (c) {
      let ctx2 = c.getContext('2d');
      ctx2.clearRect(0,0,38,38);
      ctx2.save();
      ctx2.fillStyle = opt.color;
      ctx2.beginPath();
      ctx2.arc(19, 10, 9, 0, Math.PI * 2); // Head (top)
      ctx2.fill();
      // Eyes
      ctx2.fillStyle = '#ff2222';
      ctx2.beginPath();
      ctx2.arc(19-3, 7, 1.5, 0, Math.PI*2);
      ctx2.arc(19+3, 7, 1.5, 0, Math.PI*2);
      ctx2.fill();
      // Mouth
      ctx2.strokeStyle = '#b71c1c';
      ctx2.lineWidth = 1.1;
      ctx2.beginPath();
      ctx2.arc(19, 13, 4, 0, Math.PI, false);
      ctx2.stroke();
      // Body
      ctx2.beginPath();
      ctx2.arc(19, 22, 6, 0, Math.PI*2);
      ctx2.fillStyle = opt.color;
      ctx2.globalAlpha = 0.85;
      ctx2.fill();
      ctx2.globalAlpha = 1;
      ctx2.restore();
    }
    // Draw bird (bottom) with different color for each option
    let b = document.getElementById('birdImg_' + opt.color.replace('#',''));
    if (b) {
      let ctx3 = b.getContext('2d');
      ctx3.clearRect(0,0,38,38);
      ctx3.save();
      // Pick a bird color for this slot
      let birdColor = birdShopColors[idx % birdShopColors.length];
      // Body (ellipse, bottom)
      ctx3.beginPath();
      ctx3.ellipse(19, 28, 8, 8, -0.2, 0, Math.PI * 2);
      ctx3.fillStyle = birdColor;
      ctx3.fill();
      ctx3.strokeStyle = '#b71c1c';
      ctx3.lineWidth = 1.1;
      ctx3.stroke();
      // Beak (triangle)
      ctx3.beginPath();
      ctx3.moveTo(19 + 8, 28);
      ctx3.lineTo(19 + 12, 28 - 1.5);
      ctx3.lineTo(19 + 12, 28 + 1.5);
      ctx3.closePath();
      ctx3.fillStyle = '#ffb300';
      ctx3.globalAlpha = 0.85;
      ctx3.fill();
      ctx3.globalAlpha = 1;
      // Wing (arc)
      ctx3.beginPath();
      ctx3.arc(19 - 4, 28, 4, Math.PI * 0.2, Math.PI * 1.2, false);
      ctx3.strokeStyle = '#bbb';
      ctx3.lineWidth = 1.1;
      ctx3.stroke();
      // Eye (dot)
      ctx3.beginPath();
      ctx3.arc(19 + 2, 28 - 1.5, 1.1, 0, Math.PI * 2);
      ctx3.fillStyle = '#222';
      ctx3.globalAlpha = 0.7;
      ctx3.fill();
      ctx3.globalAlpha = 1;
      ctx3.restore();
    }
  });
}
window.buySnakeColor = function(color) {
  let opt = snakeColorOptions.find(o=>o.color===color);
  if (goldCoins>=opt.cost.gold && silverCoins>=opt.cost.silver) {
    goldCoins -= opt.cost.gold;
    silverCoins -= opt.cost.silver;
    unlockedColors.push(color);
    localStorage.setItem('snakeGoldCoins', goldCoins);
    localStorage.setItem('snakeSilverCoins', silverCoins);
    localStorage.setItem('snakeColors', JSON.stringify(unlockedColors));
    updateCoinBar();
    closeShop();
    showShop();
  } else {
    alert('Not enough coins!');
  }
}
window.selectSnakeColor = function(color) {
  selectedColor = color;
  localStorage.setItem('snakeSelectedColor', color);
  closeShop();
  showShop();
}
window.closeShop = function() {
  let shop = document.getElementById('shopScreen');
  if (shop) shop.remove();
}

// --- End of Shop Logic ---

function curtainOpen() {
  curtain.style.clipPath = 'inset(0 50% 0 50%)';
  setTimeout(() => { curtain.style.display = 'none'; }, 1200);
}

function curtainClose(callback) {
  curtain.style.display = 'block';
  curtain.style.clipPath = 'inset(0 50% 0 50%)';
  setTimeout(() => {
    curtain.style.clipPath = 'inset(0 0 0 0)';
    setTimeout(callback, 1200);
  }, 50);
}

// Helper: Manhattan distance
function manhattan(a, b) {
  return Math.abs(a.x - b.x) + Math.abs(a.y - b.y);
}

// Move food away from snake if close, but only every other tick for slower movement
let foodMoveTick = 0;
function moveFoodIfNearSnake() {
  foodMoveTick = (foodMoveTick + 1) % 3; // Move only every 3rd tick
  if (foodMoveTick !== 0) return; // Skip this tick for slower bird
  const head = snake[0];
  // If snake is within 5 tiles, try to move food away
  if (manhattan(head, food) <= 5) {
    // Find all valid moves for food
    const moves = [
      {x: food.x + 1, y: food.y},
      {x: food.x - 1, y: food.y},
      {x: food.x, y: food.y + 1},
      {x: food.x, y: food.y - 1}
    ].filter(pos =>
      pos.x >= 0 && pos.x < tileCount &&
      pos.y >= 0 && pos.y < tileCount &&
      !snake.some(seg => seg.x === pos.x && seg.y === pos.y)
    );
    // Pick the move that increases distance from snake head the most
    let best = food;
    let bestDist = manhattan(head, food);
    for (let m of moves) {
      let d = manhattan(head, m);
      if (d > bestDist) {
        best = m;
        bestDist = d;
      }
    }
    // Move food if a better position is found
    if (best !== food) food = best;
  }
}

function drawSnake() {
  // Draw head as a medium-sized circle with red eyes and a mouth
  const head = snake[0];
  ctx.save();
  ctx.fillStyle = selectedColor || '#111'; // Use selected color
  ctx.beginPath();
  ctx.arc(
    head.x * gridSize + gridSize / 2,
    head.y * gridSize + gridSize / 2,
    gridSize * 0.7,
    0, Math.PI * 2
  );
  ctx.fill();
  // Eyes track the food
  let dx = food.x - head.x;
  let dy = food.y - head.y;
  let dist = Math.max(1, Math.sqrt(dx*dx + dy*dy));
  let ex = (dx / dist) * 7;
  let ey = (dy / dist) * 7;
  ctx.fillStyle = '#ff2222';
  let eye1 = {
    x: head.x * gridSize + gridSize / 2 + ex - ey/2,
    y: head.y * gridSize + gridSize / 2 + ey - ex/2
  };
  let eye2 = {
    x: head.x * gridSize + gridSize / 2 + ex + ey/2,
    y: head.y * gridSize + gridSize / 2 + ey + ex/2
  };
  ctx.beginPath();
  ctx.arc(eye1.x, eye1.y, 3, 0, Math.PI * 2);
  ctx.arc(eye2.x, eye2.y, 3, 0, Math.PI * 2);
  ctx.fill();
  // Mouth tracks food
  ctx.strokeStyle = '#b71c1c';
  ctx.lineWidth = 2;
  ctx.beginPath();
  let mouthX = head.x * gridSize + gridSize / 2 + ex * 1.2;
  let mouthY = head.y * gridSize + gridSize / 2 + ey * 1.2;
  ctx.arc(mouthX, mouthY + 7, 6, 0, Math.PI, false);
  ctx.stroke();
  ctx.restore();
  // Draw body as circles
  ctx.save();
  for (let i = 1; i < snake.length; i++) {
    ctx.beginPath();
    ctx.arc(
      snake[i].x * gridSize + gridSize / 2,
      snake[i].y * gridSize + gridSize / 2,
      gridSize * 0.5,
      0, Math.PI * 2
    );
    ctx.fillStyle = selectedColor || '#111'; // Use selected color
    ctx.fill();
    ctx.strokeStyle = '#333';
    ctx.lineWidth = 1;
    ctx.stroke();
  }
  ctx.restore();
}

function drawFood() {
  // Draw food as a bird: ellipse body same size as snake head, triangle beak, arc wing
  ctx.save();
  let cx = food.x * gridSize + gridSize / 2;
  let cy = food.y * gridSize + gridSize / 2;
  // Body (ellipse, slightly smaller than snake head)
  ctx.beginPath();
  ctx.ellipse(cx, cy, gridSize * 0.6, gridSize * 0.6, -0.2, 0, Math.PI * 2);
  ctx.fillStyle = '#fff'; // White bird body
  ctx.fill();
  ctx.strokeStyle = '#b71c1c';
  ctx.lineWidth = 1.2;
  ctx.stroke();
  // Beak (triangle)
  ctx.beginPath();
  ctx.moveTo(cx + gridSize * 0.6, cy);
  ctx.lineTo(cx + gridSize * 0.78, cy - gridSize * 0.09);
  ctx.lineTo(cx + gridSize * 0.78, cy + gridSize * 0.09);
  ctx.closePath();
  ctx.fillStyle = '#ffb300'; // Yellow beak
  ctx.globalAlpha = 0.85;
  ctx.fill();
  ctx.globalAlpha = 1;
  // Wing (arc)
  ctx.beginPath();
  ctx.arc(cx - gridSize * 0.22, cy, gridSize * 0.21, Math.PI * 0.2, Math.PI * 1.2, false);
  ctx.strokeStyle = '#bbb'; // Light gray wing for contrast
  ctx.lineWidth = 1.2;
  ctx.stroke();
  // Eye (dot)
  ctx.beginPath();
  ctx.arc(cx + gridSize * 0.15, cy - gridSize * 0.10, 1.7, 0, Math.PI * 2);
  ctx.fillStyle = '#222';
  ctx.globalAlpha = 0.7;
  ctx.fill();
  ctx.globalAlpha = 1;
  ctx.restore();
  // Animate "eating" effect if snake is eating
  if (snake[0].x === food.x && snake[0].y === food.y) {
    ctx.save();
    ctx.globalAlpha = 0.5;
    ctx.fillStyle = '#ffe066';
    ctx.beginPath();
    ctx.arc(cx, cy, gridSize * 0.6, 0, Math.PI * 2);
    ctx.fill();
    ctx.restore();
  }
}

function drawGrid() {
  // Draw realistic grass background
  ctx.save();
  ctx.fillStyle = '#6dbf4b'; // Base grass green
  ctx.fillRect(0, 0, 600, 600);
  // Draw varied grass blades
  for (let i = 0; i < 180; i++) {
    let gx = Math.random() * 600;
    let gy = Math.random() * 600;
    let bladeLen = 10 + Math.random() * 10;
    let angle = Math.random() * Math.PI / 3 - Math.PI / 6;
    ctx.save();
    ctx.translate(gx, gy);
    ctx.rotate(angle);
    ctx.beginPath();
    ctx.moveTo(0, 0);
    ctx.lineTo(0, bladeLen);
    ctx.strokeStyle = Math.random() > 0.5 ? '#7ed957' : '#4fa94d';
    ctx.lineWidth = Math.random() > 0.7 ? 2 : 1;
    ctx.globalAlpha = 0.7 + Math.random() * 0.3;
    ctx.stroke();
    ctx.globalAlpha = 1;
    ctx.restore();
  }
  // Draw small grass flowers (animated)
  const flowerColors = ['#f7e96b', '#ffb3c6', '#a3e4f7', '#f7a6e0', '#fff', '#f7c36b'];
  const flowerCount = 30;
  const flowerTime = Date.now() / 900;
  for (let i = 0; i < flowerCount; i++) {
    // Use fixed base positions for each flower for consistent animation
    let baseX = (i * 197 + 83) % 600;
    let baseY = (i * 113 + 41) % 600;
    // Animate with a gentle sway and bob
    let sway = Math.sin(flowerTime + i) * 4;
    let bob = Math.cos(flowerTime * 1.2 + i * 0.7) * 2;
    let fx = baseX + sway;
    let fy = baseY + bob;
    let color = flowerColors[i % flowerColors.length];
    ctx.save();
    ctx.beginPath();
    ctx.arc(fx, fy, 3 + Math.sin(flowerTime + i) * 1.2, 0, Math.PI * 2);
    ctx.fillStyle = color;
    ctx.globalAlpha = 0.85;
    ctx.fill();
    // Optionally add a yellow center for some flowers
    if (i % 2 === 0) {
      ctx.beginPath();
      ctx.arc(fx, fy, 1.2, 0, Math.PI * 2);
      ctx.fillStyle = '#ffe066';
      ctx.globalAlpha = 0.9;
      ctx.fill();
    }
    ctx.globalAlpha = 1;
    ctx.restore();
  }
  // Draw trees at fixed positions with animated swaying and natural shapes
  const treePositions = [
    {x: 2, y: 3}, {x: 25, y: 5}, {x: 8, y: 25}, {x: 20, y: 20}, {x: 27, y: 27}
  ];
  const t = Date.now() / 1800; // Slower, more natural movement
  treePositions.forEach((pos, idx) => {
    let tx = pos.x * gridSize + gridSize / 2;
    let ty = pos.y * gridSize + gridSize / 2;
    // Trunk
    ctx.fillStyle = '#8d5524';
    ctx.fillRect(tx - 3, ty + 10, 6, 16);
    // Animate sway: subtle, natural
    let sway = Math.sin(t + idx * 1.5) * 3.5;
    // Draw natural tree top: cluster of circles/ellipses
    ctx.save();
    let leafCenters = [
      {dx: 0, dy: 0, r: 16, a: 0},
      {dx: -10, dy: -7, r: 11, a: 0.2},
      {dx: 10, dy: -6, r: 10, a: -0.2},
      {dx: -7, dy: 8, r: 8, a: 0.1},
      {dx: 8, dy: 7, r: 9, a: -0.1}
    ];
    leafCenters.forEach((leaf, i) => {
      ctx.beginPath();
      ctx.ellipse(
        tx + sway + leaf.dx,
        ty + leaf.dy,
        leaf.r,
        leaf.r * (0.8 + 0.2 * Math.sin(t + idx + i)),
        leaf.a,
        0, Math.PI * 2
      );
      ctx.fillStyle = i === 0 ? '#388e3c' : (i % 2 === 0 ? '#43ea5e' : '#2e7d32');
      ctx.globalAlpha = 0.9 - i * 0.1;
      ctx.shadowColor = '#2e7d32';
      ctx.shadowBlur = i === 0 ? 8 : 0;
      ctx.fill();
      ctx.shadowBlur = 0;
      ctx.globalAlpha = 1;
    });
    // Add flowers and fruits
    let flowerColors = ['#fff', '#f7e96b', '#ffb3c6', '#f7a6e0'];
    let fruitColors = ['#e74c3c', '#ff9800'];
    for (let f = 0; f < 6; f++) {
      let angle = Math.random() * Math.PI * 2;
      let dist = 7 + Math.random() * 8;
      let fx = tx + sway + Math.cos(angle) * dist + (Math.random() - 0.5) * 3;
      let fy = ty + Math.sin(angle) * dist + (Math.random() - 0.5) * 3;
      ctx.beginPath();
      ctx.arc(fx, fy, 1.7, 0, Math.PI * 2);
      ctx.fillStyle = flowerColors[Math.floor(Math.random() * flowerColors.length)];
      ctx.globalAlpha = 0.85;
      ctx.fill();
      ctx.globalAlpha = 1;
    }
    for (let f = 0; f < 3; f++) {
      let angle = Math.random() * Math.PI * 2;
      let dist = 8 + Math.random() * 7;
      let fx = tx + sway + Math.cos(angle) * dist + (Math.random() - 0.5) * 2;
      let fy = ty + Math.sin(angle) * dist + (Math.random() - 0.5) * 2;
      ctx.beginPath();
      ctx.arc(fx, fy, 2.2, 0, Math.PI * 2);
      ctx.fillStyle = fruitColors[Math.floor(Math.random() * fruitColors.length)];
      ctx.globalAlpha = 0.9;
      ctx.fill();
      ctx.globalAlpha = 1;
    }
    ctx.restore();
  });
  ctx.restore();
  // Draw grid lines
  ctx.strokeStyle = '#333';
  ctx.lineWidth = 1;
  for (let i = 1; i < tileCount; i++) {
    ctx.beginPath();
    ctx.moveTo(i * gridSize, 0);
    ctx.lineTo(i * gridSize, 600);
    ctx.stroke();
    ctx.beginPath();
    ctx.moveTo(0, i * gridSize);
    ctx.lineTo(600, i * gridSize);
    ctx.stroke();
  }
}

function randomFood() {
  let pos;
  do {
    pos = {
      x: Math.floor(Math.random() * tileCount),
      y: Math.floor(Math.random() * tileCount)
    };
  } while (snake.some(seg => seg.x === pos.x && seg.y === pos.y));
  return pos;
}

function resetGame() {
  snake = [{x: 15, y: 15}];
  direction = {x: 0, y: -1};
  food = randomFood();
  score = 0;
  speed = 120;
  isGameOver = false;
  birdsEaten = 0;
  scoreElem.textContent = 'Score: 0';
  speedValueElem.textContent = speed;
  gameOverElem.style.display = 'none';
  highScore = Number(localStorage.getItem('snakeHighScore') || 0); // Reload high score from storage
  selectedColor = localStorage.getItem('snakeSelectedColor') || unlockedColors[0];
  updateHighScore();
  updateCoinBar();
}

function changeSpeed(delta) {
  speed = Math.max(MIN_SPEED, speed + delta);
  speedValueElem.textContent = speed;
}

function updateHighScore() {
  if (score > highScore) {
    highScore = score;
    localStorage.setItem('snakeHighScore', highScore);
  }
  highScoreElem.textContent = highScore;
}

function gameTick() {
  if (isGameOver) return;
  speedValueElem.textContent = speed;
  const head = {x: snake[0].x + direction.x, y: snake[0].y + direction.y};

  // Wall collision
  if (head.x < 0 || head.x >= tileCount || head.y < 0 || head.y >= tileCount) {
    return endGame();
  }
  // Self collision
  if (snake.some(seg => seg.x === head.x && seg.y === head.y)) {
    return endGame();
  }

  snake.unshift(head);

  // Eat food
  if (head.x === food.x && head.y === food.y) {
    score++;
    birdsEaten++;
    // Award coins randomly: 30% gold, 70% silver
    if (Math.random() < 0.3) {
      goldCoins++;
      localStorage.setItem('snakeGoldCoins', goldCoins);
    } else {
      silverCoins++;
      localStorage.setItem('snakeSilverCoins', silverCoins);
    }
    updateCoinBar();
    food = randomFood();
    speed = Math.max(MIN_SPEED, speed - 3); // Apply speed limit
  } else {
    snake.pop();
    // Move food if snake is near
    moveFoodIfNearSnake();
  }

  // Draw everything
  ctx.clearRect(0, 0, 600, 600);
  drawGrid();
  drawSnake();
  drawFood();

  gameLoop = setTimeout(gameTick, speed);
}

function endGame() {
  isGameOver = true;
  clearTimeout(gameLoop);
  updateHighScore();
  // Show analysis and shop after curtain
  curtainClose(() => {
    finalScoreElem.innerHTML = 'Final Score: ' + score + '<br>High Score: ' + highScore +
      `<br>Birds Eaten: ${birdsEaten}<br>Gold Coins: ${goldCoins} <span style='color:gold;'>&#x1F7E1;</span> Silver Coins: ${silverCoins} <span style='color:silver;'>&#x26AA;</span>`;
    gameOverElem.style.display = 'block';
    setTimeout(showShop, 1200);
  });
}

function restartGame() {
  resetGame();
  curtainOpen();
  setTimeout(gameTick, 1200);
}

function startGame() {
  document.getElementById('introScreen').style.display = 'none';
  resetGame();
  curtainOpen();
  setTimeout(gameTick, 1200);
}

document.addEventListener('keydown', e => {
  if (isGameOver) return;
  if (e.key === 'ArrowUp' && direction.y !== 1) direction = {x: 0, y: -1};
  else if (e.key === 'ArrowDown' && direction.y !== -1) direction = {x: 0, y: 1};
  else if (e.key === 'ArrowLeft' && direction.x !== 1) direction = {x: -1, y: 0};
  else if (e.key === 'ArrowRight' && direction.x !== -1) direction = {x: 1, y: 0};
});

// Start the game
document.getElementById('introScreen').style.display = '';
// Do not auto-start, wait for user to click Start Game
highScore = Number(localStorage.getItem('snakeHighScore') || 0);
updateHighScore();
```
