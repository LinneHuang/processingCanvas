# Class Notes

--
--
--


### 0927 "Cloudy" Drawing with an Image

```
PImage cloud;

void setup() {
  size(800, 800);
  noStroke();
  fill(255, 50);
  
  cloud = loadImage("cloud.png");
  imageMode(CENTER);
  background(#ffffff);
  noCursor();
}

void draw() {
  image(cloud, mouseX, mouseY, 200, 200);
}

void mousePressed() {
  tint(random(255), random(255), random(255), random(30));
  //tint(255, random(50));
  //saveFrame("myPicture" + "frameCount.png");
  saveFrame("myPicture####.png");
}
```
--

### 0927 Triggering Animations with a boolean variable (click to make clouds rise)

```
//float ballsHeight = 750;

//void setup() {
//  size(800, 800);
//}

//void draw() {
//  // setup
//  background(#818181);
//  ballsHeight -= 5;
  
//  pushMatrix();
//    translate(width / 2, ballsHeight);
//    noStroke();
//    fill(255, 50);
//    ellipse(10, 10, 40, 40);
//    ellipse(17, 30, 40, 40);
//    ellipse(-17, 34, 40, 40);
//  popMatrix();
  
  
//  if (ballsHeight <= 50)  {
//   ballsHeight = 750;
//   } else {
//   println("come back");
//   }
  
//}

float cloudHeight = 0;
boolean isAnimating = false;
int selectedColor = 0;


void setup() {
  size(800,800);
  cloudHeight = 800;
  noStroke();
  fill(90, 255);
}

void draw() {
  // logic
  if (selectedColor == 0) {
    fill(0, 0, 255, 70);
  }
  
  if (mouseY > 600) {
    isAnimating = true;
  }
  
  if (isAnimating) {
    cloudHeight -= 4;
  }
  println(selectedColor);
  
  background(0);
  pushMatrix();
    translate(width / 2, cloudHeight);
      noStroke();
      ellipse(10, 10, 40, 40);
      ellipse(17, 30, 40, 40);
      ellipse(-17, 34, 40, 40);
  popMatrix();
}

void mousePressed() {
  selectedColor += 1;
  isAnimating = !isAnimating;
}
```
--

### More: Move the mouse to change the background color

```
// Move the mouse across the image
// to change its value

int value = 0;

void setup() {
  size(500, 500);
}

void draw() {
  fill(value);
  rect(25, 25, 400, 400);
}

void mouseMoved() {
  value = value + 5;
  if (value > 255) {
    value = 0;
  }
}
```
--

### More: Classic Processing 101— just drawing a bunch of circles

```
// just drawing many round shapes

void setup() {
 size(800, 800);
 map(mouseX, 0, 800, 300, 678);
}

void draw() {
ellipse(mouseX, mouseY, 20, 20);
}
```

--

### 0920 Quiz: Growing Bubbles in Blue Canvas

```
//160920 quiz! + tutorial

float ballHeight = 650;
float bubbleSize = 0;
float gradually = 0;

void setup() {
 size(800, 800);
 
 ballHeight = height - 100;
 background(#317EFF); // only "draw" background once
 
 stroke(245, 245, 245, 50);
 noFill();
}

void draw() {
  // // logic
  ballHeight = ballHeight - 5;
  bubbleSize = bubbleSize + 5.0;
  println("ballHeight = " + ballHeight);
  
  // if the ball is too far up
  // bring the ball back down
  if (ballHeight <= 0)  {
   ballHeight = 800;
   bubbleSize = 0;
 } else {
   println("I'm rolling");
 }
  
  
  
  // // draw
  //background(#317EFF);
  ellipse(gradually++, ballHeight, bubbleSize, bubbleSize);
}


////////////////////////////////////
//// extra notes on assignments ////
////////////////////////////////////
// 1. mapping: set the boundary
//    float varOne;
//    varOne = map(mouseX, 0, width, 244, 590);
//    float varTwo;
//    varTwo = map(mouseY, 0, height, 244, 590);
//
// 2. translate, and pushMatrix + popMatrix
//    tranlate(400, 100); -> change the position
//    pushMatrix + popMatrix -> set the range of variations / animations
//
// 3. colorMode(HSB);
// 4. frameRate(30);
// 5. 
```
--

### 0913 Little house, lawn, moon and darker and darker sky

```
float moonHeight = 350;
float blueValue = 255;

// set up the size of canvas
void setup() {
    size(800, 700);
    
    // integer for RGB
  int r = 136;
  int g = 213;
  int b = 198;
  
  int myStrokeWeight = 3;
  
  for (int i = 0; i < height; i++) {
    // let i change R/G/B value
    stroke(mouseX, mouseY, b);
    // make gradient with lines
    line(0, i, width, i);
  }
}


void draw() {
    
    //moonHeight = moonHeight - 0.2;
    moonHeight = random(moonHeight) - 0.1;
    blueValue = blueValue - 1;
    
    //println
    println("x: "+ mouseX);
    println("y: "+ mouseY);
    
    background(31, 4, blueValue);
    
    //moon
    noStroke();
    fill(mouseX, 255, mouseY);
    ellipse(mouseX, 100, 100, 100);
    
    //horizon
    stroke(#ffffff);
    line(0, 475, 800, 476);
    
    //roof
    noStroke();
    fill(#FF5F43);
    triangle(500, 408, 450, 450, 500+50, 450);
    
    //house body
    noStroke();
    fill(#ffffff);
    rect(460, 450, 80, 41);
    
    //door
    noStroke();
    fill(#000000);
    rect(493, 471, 16, 20, 15, 15, 0, 0);
}

void mousePressed() {
  stroke(203, 234, 44, 80);
}

```
--

### 0906 Colored Ripple

```
float circleSize = 0;

void setup() {
  size(800, 800);
  background(0);
  
  noFill();
  stroke(255, 125, 180, 50);
}

void draw() {
  circleSize = circleSize + 1;
  ellipse(mouseX, mouseY, circleSize, circleSize);
}

void mousePressed() {
  stroke(203, mouseY, 44, 80);
}
```