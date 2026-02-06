```
let playerX;
let score = 0;

// TASK 1: Define the initial state of the coin object
let coin = {
  cx: 200,
  cy: 0, // how do yo start off-screen?
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

  // TASK 3: Pass the coin's data into the drawing function
  drawCoin( /* FILL IN */ );

  // TASK 5: Use the checkHit function. 
  // Compare the player position (playerX, 370) with the coin position

  if (checkHit( /* FILL IN */ )) {
    score++;
    resetCoin();
    coin.speed += 0.5;
  }
}

function drawPlayer() {
  fill(255, 200, 0);
  playerX= mouseX;
  rect(playerX- 25, 370, 50, 15);
}

// TASK 2: Use the parameters (cx, cy, s) to draw the ellipse
function drawCoin(/* FILL IN */) {
  fill(255, 255, 0);
  // Hint: use the parameter names here, not the object name
  ellipse( /* FILL IN */, /* FILL IN */, /* FILL IN */ );
}

function moveCoin() {
  coin.cy += coin.speed;
  
  // TASK 5: What happens if the coin falls past the bottom?
  if (coin.cy > height) {
    /* FILL IN: reset the coin and the score */
  }
}

// TASK 4: Complete the logic. What does draw() need to hear back?
function checkHit(x1, y1, x2, y2) {
  let d = dist(x1, y1, x2, y2); 
  // add text so show the distance so we can varify its working.


  // This needs to return a true or false value
  if (d < 30) {
    /* FILL IN */
  } else {
    /* FILL IN */
  }
}

function resetCoin() {
  // Randomize X and reset Y to a negative number to delay the fall
  coin.cx = random(20, width - 20);
  coin.cy = random(-100, -20); 
}

function displayScore() {
  fill(255);
  textSize(18);
  text(`Score:  ${score}`, 20, 30)
}
```
