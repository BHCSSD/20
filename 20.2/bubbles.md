## 1. Review: Variables vs Objects

Instead of managing separate, disconnected arrays for cx and cy positions, we put all data into a single container called an **Object**.

| Method | Syntax | 
| --- | --- |
| **Variables** | `let cx = 20` | 
| **Objects** | `let ball = { cx: 20, cy: 30 }` | 

---

## 2. Loading the Array

To create a population of objects, we declare an empty array and use a `for` loop to fill it with object literals.

```javascript
let bubbles = []//im empty... so sad

function setup() {
  createCanvas(400, 400);

  // Fill the array with 10 unique object literals
  for (let i = 0; i < 10; i++) {
    bubbles.push( {
      

      } )
  }//end of for
}//end setup

```

---

## 3. Display and Update 

Use a loop to iterate through the array. We access the data inside each object using **Dot Notation** `bubbles[i].cx`
> [!note]
> **Dot Notation** is the syntax used to "peek inside" an object to access its data. 
>
> **Iteration** is the computer science term for **repetition**.
> - When we use a `for` loop to go through an array, we are "iterating" over the collection, performing the same set of instructions for every single object in the list, one by one.
> - 

```javascript
function draw() {
  background(30);
  fill(0, 150, 255, 150);
  noStroke();

  for (let i = 0; i < bubbles.length; i++) {
    // 1. Make a local var to reference the current object
  
    
    // 2. Use the object's properties to draw an circle
    
    
    // 3. Update the object's properties (Animation)

    
    // 4. Reset logic
    if (b.cy > height + b.r) {

    }//end of if
  }//end of for


}//end fo draw

```

## TODO:
 * Add a `colour` property to the object in `setup()`. Use `fill(b.colour)` inside the loop to give every object its own colour that changes every time it resets
