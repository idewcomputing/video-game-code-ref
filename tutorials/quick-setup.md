# Quick Setup 🚀

The standard setup for our phaser game is outlined below. You will have three main files -- _index.html_, _script.js_, and _style.css_, along with a folder for _assets_.

* **index.html**
* **script.js**
* **style.css**
* **assets** _\(a folder for images and sound effects\)_

**Create the three files and folder with your code editor \(e.g. replit.com\) and proceed to get the game starter code below.** 

## index.html

**Starting with an empty index.html file \(you may have to delete content\), copy and paste the html below into your** _index.html_ **file.** Notice how the _style.css_ file and _script.js_ files are linked in the html. The `<div id="game"></div>` element will contain the video game presented in the browser. You can update the `h1` element and `p` element to present the game title and author name you prefer.

```markup
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Game Title</title>
    <link href="style.css" rel="stylesheet" type="text/css">
  </head>
  <body>
    <div id="my-game"></div>
    <h1>Game Title</h1>
    <p>Coded by ...</p>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/phaser-ce/2.13.2/phaser.min.js"></script>
    <script src="script.js"></script>
  </body>
</html>
```

## style.css

**Copy and paste the css below into your style.css file.** Notice how this simply sets the width and height of the game and places a border around it. The `auto` part in the margin automatically sets the left and right margins to the game equally so that the game is centered in the browser window.

```css
#my-game {
  width: 800px;
  height: 600px;
  margin: 0 auto;
  border: 1px solid black;
}
```

## script.js

**Copy and paste the Javascript below into your script.js file.** Notice the comments \(lines beginning with `//`\) in the code that describe the `game` variable and the primary functions used in a phaser game.

```javascript
// create Phaser.Game object assigned to global variable named game
var game = new Phaser.Game(800, 600, Phaser.AUTO, 'my-game', { preload: preload, create: create, update: update });

// declare other global variables (for sprites, etc.)


// preload game assets - runs one time when webpage first loads
function preload() {

}

// create game world - runs one time after preload finishes
function create() {

}

// update game - runs repeatedly in loop after create finishes
function update() {

}

// add custom functions (for collisions, etc.) - only run when called
```

### 🎉 Now you are all set to complete the game tutorial!



