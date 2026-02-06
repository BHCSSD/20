# Pong

### Step 1: The Setup & Global Variables
 Define the "state" of our game. These variables need to be outside any function so every part of our program can see them.

```javascript
let ballX, ballY, ballSpeedX, ballSpeedY
let playerY
const paddleHeight = 80

function setup() {
  createCanvas(600, 400);
  ballX = width /2
  ballY = height/ 2
  ballSpeedX = 5
  ballSpeedY = 2
  playerY = height/2
}

```

### Step 2: Creating the "Game Loop"

**Task:** Add these function calls to your `draw()` function, even though we haven't written the logic for them yet!

```javascript
function draw() {
  background(0);
  
  moveElements()// Logic
  showElements()// Visuals
}

```

---

### Step 3: Drawing the Elements

Ndefine what `showElements()` actually does. Use the coordinates defined in our variables to place shapes.

```javascript
function showElements() {
  fill(255);

  ellipse(ballX, ballY, 15)// Draw the ball

  rect(10, playerY, 10, paddleHeight)  // Draw the player paddle
}

```

---

### Step 4: Adding Movement Logic

Now we need to make things move. This is where the math happens. To move the ball, we add its speed to its position every frame.

**Task:** Write the `moveElements` function. We will also make the paddle follow the mouse.

```javascript
function moveElements() {
  // Move the ball

  
  // Move the paddle with the mouse

}

```

---

### Step 5: Collision and Bouncing

The ball now flies off the screen. We need to check if the ball hits the edges.

**TODO** * If `ballY` is less than 0 or greater than the `height`, reverse `ballSpeedY`.

* If the ball hits the paddle, reverse `ballSpeedX`.

```javascript
function checkBounces() {
  // Ceiling and Floor

  
  // Simple Paddle Hit (Left side)

}

```

**Important:** Don't forget to call `checkBounces()` inside your `draw()` function

---

## Challenge

Now that you have a moving ball and a paddle, try to complete the game on your own:

1. **Add a Reset:** Create a function `resetBall()` that puts the ball back in the middle if it goes past the left or right edge.
2. **Add a Score:** Create a `score` variable and use the `text()` function to display it on the screen.
3. **The Opponent:** Can you create a second paddle on the right side that automatically follows the `ballY` position?

