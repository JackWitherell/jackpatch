# jackpatch

jackpatch is a simple short processing file that handles a few functions
- enhanced keyboard input handling
- easy error alerting
- image loading with error handling

# How to use
### Enhanced Keyboard Input Handling
`keys.isPressed(char/string)` will return the `boolean` (true/false) state of if the input `char/string` key is pressed or not. This uses the `keyPressed` and `keyReleased` event handlers so it might be useful to include a call to your own controller in there. This kind of keyboard input handling should simply be used for quick editing of processing sketches unless its implementation is all that's needed within the scope of issuing events during runtime (such as isolating all main update logic to the draw loop, not recommended for performance).

This code example will run rapidTri if a is pressed and it will run dispObj if the s key is pressed (but not if the a key is pressed due to if/else if precedence)
```java
  if(keys.isPressed('a')){
    rapidTri();
  }
  else if(keys.isPressed('s')){
    dispObj(true);
  }
```
### Easy Error Alerts
`error(String, Boolean)` will create a javax swing alert box that will print the input `string`. If the input `boolean` (true/false) value is true, the alert will be an info box, and the program pause until ok is clicked. If false, the alert will be an error box and the program will close after ok is clicked.

These could be used in lieu of breakpoints in a beginning programming environment or just to be used as trivial error handlers.

This piece of code will create an error box that will print out the string error and quit the program when the if condition is true.
```java
if(temp==null){
  error("Assets are Missing! ("+path+")", false);
}
```
### Image Loading with Error Handling
This Override's Processing's `loadImage(String)` function to include error handling. By default Processing returns `null` when an image cannot be found and also prints to the console that it couldn't be found. In these cases when rapidly prototyping programs I've always found myself having to write workarounds in code to figure out whether or not an asset is actually being loaded in. This fixes that by telling you outright using an alert box.

Use the loadImage function as you would normally, and it will return an error when the asset is missing.
```java
PVector position;
PImage visual;
UIObject(){
  position=new PVector(0,0);
  visual=loadImage("data/broken.png");
}
```

# Who is this for?
jackpatch is mainly for me, hence my name being in it, but it can also be used by beginners to learn a bit about how some classes and functions can be changed modularly in object oriented programming languages. This is a set of code that I'll likely carry and modify between projects in order to create some easy debugging cases between sketches and other applications.