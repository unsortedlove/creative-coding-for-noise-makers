# creative-coding-for-noise-makers


## program

### intro
- what is unsorted
- what is creative coding
- p5, hydra, strudel and why do we use them



### audio


### video

#### p5
- p5js ref https://p5js.org/reference/
- js reference mdn https://developer.mozilla.org/en-US/docs/Web/JavaScript

- basic setup
```javascript
function setup(){ 
	createCanvas(windowWidth, windowHeight); // declares size of output window 
	background(0); // creates a black background 
} 
 
function draw(){ 
	// main code will go here! 
} 
```

- basic shapes
```javascript
line(0, 0, width, height); // draws line from x1, y1 to x2, y2 
// rectMode(CENTER); // to draw center out 
rect(width/2, height/2, height/4, height/4); // draws rectangle at given postition and size (width, height) 
ellipse(width/2, height/2, height/4, height/4); // draws ellipse at given postition and size 
```

- fill
- stroke
- colors


mouse interaction

```javascript
// mouseX » x position of x mouse 
// mouseY » y position of mouse 
// pmouseX, pmouseY » returns previous position (one draw cycle before) 
 
line(mouseX, mouseY, pmouseX, pmouseY); // worlds simplest drawing program in 3..2..! 

// map(inputVariable, inputMin, inputMax, outputMin, outputMax); 
let mySize = map(mouseX, 0, width, 1, 20); 
strokeWeight(mySize); 
```

variables

```javascript
let mySpeed = 5; // this is for a whole number 
let mySpeed = 5.243; // this is for a number with decimal points 
let myText = "text goes here"; // variable for text 
let myToggle = true; // stores true or false, useful for a switch 
let myArray = [45, 12, 52, 22]; // stores group of variables, can be anything! 


let x = 0; // global and declared/set only once 
 
function setup(){ 
    createCanvas(windowWidth, windowHeight); 
} 
 
function draw(){ 
    background(0); 
    let s = 50; // won't change.. re-declared constantly here 
    rect(x, s, s, s); // 's' is used multiple times 
 
    x += 5; // 'x' gets bigger and bigger 
} 
```

- noise (random walker)
- audio reactivity..

advance
- random
- conditional
- for loops, grids

#### hydra
- hydra online https://hydra.ojack.xyz/?sketch_id=example_6
- hydra docs https://hydra.ojack.xyz/docs/
- interactive documentation https://hydra.ojack.xyz/api/

- sources: noise, voronoi, osc, external sources
- for now: input p5, how you work with sources
- geometry
- modulate (modulate, modulateScale)
- blend
- audio (fft)




### test perf
