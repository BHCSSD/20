# 20

**p5.js Code Style Guide: Tidy Code**
### Style Rules

1. **2 Empty Lines Between Functions**
    - Always leave two blank lines between top-level function definitions (between `setup()` and `draw()`).
2. **1 Empty Line Between Control Blocks**
    - Separate distinct code blocks—such as `if` statements and `for` loops—with a single empty line before and after.
3. **Consistent Indentation Levels**
    * All code inside a function body is indented by 1 level.
    * All code inside an `if()` statement body is indented by 1 additional level.
    * All code inside a `for` loop body is indented by 1 additional level.
    * Code placed between `push()` and `pop()` should be indented by 1 extra level to clearly highlight state transformations.


4. **Scope Termination Comments**
    - Add `//end of ...` comments immediately following the closing brace `}` for functions, `if` statements, and loops

5. **Remove any print statements**

6. **Make sure there are no Erors**

7. **Remove any dead code**
   - If there is any code that is commented out, remove it.
   - If there is code/ variables / functions not being used, remove it. 
---

### Example

```javascript
function setup() {
  createCanvas(400, 400)
} //end of setup


function draw() {
  background(220)

    for (let i = 0; i < 5; i++) {
      let spacing = i * 50
      circle(50+spacing, 200+spacing,44)
    } //end of for

    if (x > 100) {
        ellipse(200, 200, 40, 40)
    }else if(x < 20){
        rect(200, 200, 40, 40)
    } else{
        triangle(200, 200,111,200,300,300)
    }//end of if

  push()
    stroke(0)
    fill(255, 0, 0)
  pop()

} //end of draw

```
