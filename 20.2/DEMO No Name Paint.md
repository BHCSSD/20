```js
let colours = [];
let selectedColour;
let boxSize = 50;

function setup() {
  createCanvas(400, 400)
  background(222)

  // 2. THE ARRAY: Storing our color data
  // add more colours until the palate goes across the screen
  // use random() to help
  colours = [
    color(255, 0, 0),
    color(0, 255, 0), 
    color(0, 0, 255), 
    color(0)         
  ]

  selectedColour = colors[3]; // Initialize with Black
}

function draw() {
  // 1.Draw the the palette from the array with rects and fill
  for (let i = 0; i < colours.length; i++) {

    
  }//end of for

  // 3. Logic for picking vs. painting
  
  
  
  
  
}//end of draw

```
