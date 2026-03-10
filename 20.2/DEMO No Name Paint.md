```js
let colours = [];
let brushColor;
let boxSize = 50;

function setup() {
  createCanvas(400, 400)
  background(222)

  // 2. THE ARRAY: Storing our color data
  // add more colours until the palate goes across the screen
  colours = [
    color(255, 0, 0), // Index 0: Red
    color(0, 255, 0), // Index 1: Green
    color(0, 0, 255), // Index 2: Blue
    color(0)         //Index 3: Black
  ]

  brushColor = colors[3]; // Initialize with Black
}

function draw() {
  // 1.Draw the the palette from the array with rects and fill
  for (let i = 0; i < colours.length; i++) {

    
  }//end of for

  // 3. Logic for picking vs. painting
  
  
  
  
  
}//end of draw

```
