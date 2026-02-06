```
let playerX;
let score = 0;

// TASK 1: Define the initial state of the coin object
let coin = {
  x: 200,
  y: 0, // change Y so it starts higher
  size: 25,
  speed: 5
};

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(50, 100, 150);
  
  drawPlayer();
  displayScore();
  moveCoin();

  // TASK 2: Pass the coin's data into the drawing function
 // drawCoin( /* FILL IN */       );

  // TASK 5: Use the checkHit function. 
  // What 4 variables does it need to compare?
  if (checkHit( /* FILL IN */ )) {
    score++;
    resetCoin();
    coin.speed += 0.5;
  }
}

function drawPlayer() {
  fill(255, 200, 0);
  playerX = mouseX;
  rect(playerX - 25, 370, 50, 15);
}

// TASK 3: Use the parameters (cx, cy, s) to draw the ellipse
function drawCoin( /* FILL IN */ ) {
  fill(255, 255, 0);
  ellipse( /* FILL IN */, /* FILL IN */, /* FILL IN */ );
}

function moveCoin() {
  coin.y += coin.speed;
  if (coin.y > height) {
 // TASK 5: finish this
  }
}

// TASK 4: Complete the logic. What does draw() need to hear back?
function checkHit(x1, y1, x2, y2) {
  let d = dist(x1, y1, x2, y2);
  if (d < 30) {
    /* FILL IN */
  } else {
    /* FILL IN */
  }
}

function resetCoin() {
  coin.x = random(20, width - 20) 
  coin.y = 0 // randomize this 
}

function displayScore() {
  fill(255);
  textSize(18);
  text("Score: " + score, 20, 30);
}

```
