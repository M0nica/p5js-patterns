# p5.js

Notes on random [p5.js](https://p5js.org/) coding patterns

## Table of Contents
- [Positioning Elements](#positioning-elements)
- [Responding to User Input](#responding-to-user-input)

## Positioning Elements
### centering elements
```js
function draw() {
  background(220);
  /* center element by setting x value to half the width of the canvas and the y value as half the height of canvas */
  circle(width/2,height/2,100)
}
```
[View example in p5.js editor](https://editor.p5js.org/M0nica/sketches/nkt3ee0TJ)


## Responding to User Input
### save canvas as image when 's' key is pressed

```js
function keyReleased() {
// save canvas as processing-image.png when the 's' key is pressed
  if (key == "s" || key == "S") saveCanvas(`processing-image`, "png");
}
```
[View example in p5.js editor](https://editor.p5js.org/M0nica/sketches/voKY0hf8L)

---

### use actRandomSeed() to only update random values when triggered by user input
```js
/* Function calls to random() always returns the same function when randomSeed() has the same seed parameter.
Instead of the default behavior where random seed paramater changing each time the draw() function is called, 
i.e, 60x a minute it'll only be called when mousePressed() or keyPressed() */

let actRandomSeed;

function setup() {
  createCanvas(500, 500);
  actRandomSeed = int(random(0,4))
  
}

function draw() {
  clear();
  background("#f8eeff");
  // comment out the next line to see how the random values change automatically without clicking or pressing any keys.
 randomSeed(actRandomSeed);
 
  textSize(40);
// display integer between 0,4 based on pseudorandom output from random()
  text(int(random(0,4)), width/2, height/2);
}



function mousePressed() {
  // change randomSeed on mouse press
  actRandomSeed = random(100000);
}

function keyPressed() {
  // change randomSeed on press of any key
  actRandomSeed = random(100000);
}
```

[View example in p5.js editor](https://editor.p5js.org/M0nica/sketches/oFf16op96)
