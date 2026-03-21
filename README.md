# Creative Coding for Noise Makers

Beginner friendly workshop exploring live coding visuals and audio. We'll use [p5.js](https://p5js.org/) and [Hydra](https://hydra.ojack.xyz/) for visuals (via [P5 Live](https://teddavis.org/p5live/)), and [Strudel](https://strudel.cc/) for live-coded music.

---

## Program

### Intro

- What is [Unsorted](https://unsorted.love/)
- What is creative coding
- p5.js, Hydra, Strudel. What they are and why we use them

---

### Audio

We'll use [Strudel](https://strudel.cc/) — a live coding environment for music, running entirely in the browser.

- [Strudel tutorial](https://strudel.cc/workshop/getting-started) interactive getting-started guide
- [Strudel documentation](https://strudel.cc/learn/notes) full reference
- Explore patterns, samples, synths, and effects all from your browser

---

### Video

#### p5.js

p5.js is a JavaScript library for creative coding, with a focus on making coding accessible for artists and beginners.

- [p5.js reference](https://p5js.org/reference/)
- [JavaScript reference (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

##### Basic setup

Every p5.js sketch has two main functions: [`setup()`](https://p5js.org/reference/p5/setup) runs once at the start, and [`draw()`](https://p5js.org/reference/p5/draw) runs in a loop, roughly 60 times per second.

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight); // the canvas fills the whole window
  background(20); // dark grey background
}

function draw() {
  // everything you draw goes here
}
```

> [`createCanvas()`](https://p5js.org/reference/p5/createCanvas) · [`background()`](https://p5js.org/reference/p5/background)

##### Basic shapes

p5.js gives you simple functions to draw shapes. Coordinates start at the top-left corner: `x` goes right, `y` goes down.

```javascript
line(0, 0, width, height); // diagonal line corner to corner

rect(100, 100, 200, 150); // rectangle at x:100, y:100, 200 wide, 150 tall
// rectMode(CENTER); // uncomment to draw rectangles from their center

ellipse(width / 2, height / 2, 120, 120); // circle in the center of the canvas

triangle(300, 100, 250, 200, 350, 200); // triangle with three corner points
```

> [`line()`](https://p5js.org/reference/p5/line) · [`rect()`](https://p5js.org/reference/p5/rect) · [`ellipse()`](https://p5js.org/reference/p5/ellipse) · [`triangle()`](https://p5js.org/reference/p5/triangle) · [`rectMode()`](https://p5js.org/reference/p5/rectMode)

##### Fill, stroke & colors

Control how shapes look with fill (inside color), stroke (outline color), and strokeWeight (outline thickness). Colors can be greyscale (one value), RGB (three values), or include alpha for transparency (four values).

```javascript
fill(255, 0, 100); // bright pink fill
stroke(255); // white outline
strokeWeight(3); // 3px outline

rect(50, 50, 100, 100);

noFill(); // no fill, outline only
stroke(0, 200, 255); // cyan outline
ellipse(250, 150, 80, 80);

noStroke(); // no outline, fill only
fill(255, 200, 0, 150); // yellow, semi-transparent
ellipse(200, 120, 100, 100);
```

> [`fill()`](https://p5js.org/reference/p5/fill) · [`noFill()`](https://p5js.org/reference/p5/noFill) · [`stroke()`](https://p5js.org/reference/p5/stroke) · [`noStroke()`](https://p5js.org/reference/p5/noStroke) · [`strokeWeight()`](https://p5js.org/reference/p5/strokeWeight)

##### Mouse interaction

Use the mouse to make your sketches interactive. p5.js tracks the mouse position every frame.

```javascript
// mouseX — current x position of the mouse
// mouseY — current y position of the mouse
// pmouseX, pmouseY — mouse position from the previous frame

line(mouseX, mouseY, pmouseX, pmouseY); // a simple drawing program!

// map() converts a value from one range to another
let brushSize = map(mouseX, 0, width, 2, 30);
strokeWeight(brushSize);
```

> [`mouseX`](https://p5js.org/reference/p5/mouseX) · [`mouseY`](https://p5js.org/reference/p5/mouseY) · [`pmouseX`](https://p5js.org/reference/p5/pmouseX) · [`map()`](https://p5js.org/reference/p5/map) · [`strokeWeight()`](https://p5js.org/reference/p5/strokeWeight)

##### Variables

Variables let you store and reuse values. Use `let` to declare them.

```javascript
let speed = 3; // a whole number
let position = 12.5; // a decimal number
let label = "hello"; // text
let visible = true; // true or false — useful as a toggle
let points = [10, 20, 30, 40]; // an array — a list of values

let xPos = 0; // declared outside draw() so it persists between frames

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0);
  let size = 60; // declared inside draw() — resets every frame
  rect(xPos, height / 2, size, size);

  xPos += speed; // xPos increases each frame — the rectangle moves right
}
```

##### Noise

[`noise()`](https://p5js.org/reference/p5/noise) generates smooth, organic random values — great for natural-looking movement.

```javascript
let t = 0;

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0, 20); // slight trail effect
  let x = noise(t) * width;
  let y = noise(t + 100) * height;
  ellipse(x, y, 30, 30);
  t += 0.01; // smaller increments = smoother movement
}
```

> [`noise()`](https://p5js.org/reference/p5/noise) · [`random()`](https://p5js.org/reference/p5/random)

##### Advanced topics

Once you're comfortable with the basics, try these:

###### Random

`random()` gives you a surprise value every time it's called. Think of it like rolling a die, but you get to pick the range. It's the easiest way to make your sketches feel alive and unpredictable, because no two frames will ever look the same.

```javascript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(0, 20); // slightly transparent black — leaves ghost trails
  let x = random(width);
  let y = random(height);
  let size = random(5, 40);
  fill(random(255), random(255), random(255), 180);
  noStroke();
  ellipse(x, y, size, size); // a new random circle every frame
}
```

> [`random()`](https://p5js.org/reference/p5/random)

###### Conditionals

An `if`/`else` statement is like asking a question in your code: *if* something is true, do this, *else*, do that. It's how you make your sketch react to what's happening, like a ball bouncing off the edges of the canvas instead of flying off into the void.

```javascript
let x = 200;
let speed = 3; // how many pixels the ball moves each frame

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(30);
  fill(255, 100, 150);
  noStroke();
  ellipse(x, 200, 50, 50);

  x = x + speed; // move the ball

  // if the ball hits either edge, reverse direction
  if (x > width || x < 0) {
    speed = speed * -1; // this makes it bounce back
  }
}
```

> [`if`/`else`](https://p5js.org/reference/p5/if-else)

###### For loops & grids

A loop lets you do something many times without writing it out over and over. Instead of placing 100 circles by hand, you tell the computer "start here, end there, and repeat." Nest two loops together: one for rows, one for columns — and you get a grid with just a few lines of code.

```javascript
function setup() {
  createCanvas(400, 400);
  noLoop(); // only draw once — this is a static pattern
}

function draw() {
  background(20);
  noStroke();
  let spacing = 40; // distance between each circle

  for (let x = spacing / 2; x < width; x = x + spacing) {
    for (let y = spacing / 2; y < height; y = y + spacing) {
      let d = dist(x, y, width / 2, height / 2); // distance from center
      let size = map(d, 0, 300, 30, 5); // bigger near the center
      fill(map(d, 0, 300, 255, 50), 100, 200);
      ellipse(x, y, size, size);
    }
  }
}
```

> [`for`](https://p5js.org/reference/p5/for) · [`dist()`](https://p5js.org/reference/p5/dist) · [`map()`](https://p5js.org/reference/p5/map)

---

#### Hydra

[Hydra](https://hydra.ojack.xyz/) is a live coding video synthesizer that runs in the browser. Think analog video synthesis, but with code.

- [Hydra editor](https://hydra.ojack.xyz/?sketch_id=example_6)
- [Hydra docs](https://hydra.ojack.xyz/docs/)
- [Interactive function reference](https://hydra.ojack.xyz/api/)



##### Key concepts

- **Sources** `noise()`, `voronoi()`, `osc()`, plus external sources (webcam, screen, p5 canvas)
```javascript
noize(3,.5).out()
voronoi(3,.5).out()
osc(5,.5,1).out()
```
- **Geometry** `rotate()`, `scale()`, `pixelate()`, `kaleid()` to transform visuals
- **Modulate** `modulate()`, `modulateScale()` use one texture to distort another
- **Blend** `blend()`, `add()`, `mult()` combine layers together
- **Audio** `a.fft[]` to make visuals react to sound input
- **p5 → Hydra** feed your p5.js canvas into Hydra as a source for further processing
