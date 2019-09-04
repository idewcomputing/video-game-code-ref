# Phaser CE Game Template

Phaser games are JavaScript-powered web apps that run in a browser.

Your Phaser game will consist of an HTML file, a CSS file, and a JS file. The JavaScript file will contain your game code. You'll also have a folder containing the asset files \(images, animated sprites, sound effects, etc.\) for your game.

Your game will also need to load the Phaser CE game framework, which is a JavaScript file named `phaser.min.js` that defines classes for JS objects you'll use in your game code. You can either load this Phaser CE file from a local copy \(placed in the same location as your HTML, CSS, and JS files\) or by linking to a URL from a CDN \(Content Delivery Network\).

## Create New Files for Game

Using a code editor \(such as [repl.it](https://repl.it/)\), create a new project \(or folder\) for your game containing three new files:

* HTML file named`index.html`
* CSS file named `style.css`
* JS file named `script.js`

Depending on the code editor you're using, these new files might be completely blank — or they might have starter code that was automatically inserted by the code editor. Either way is fine. You'll add new code to each of these files.

{% hint style="info" %}
**JS FILENAME:**  This code guidebook will refer to `script.js` as the name of the JS file containing your Phaser game code. However, you can choose a different name for this file \(such as `code.js` or `game.js`\). You'll just need to be sure the `<script>` tag in your HTML lists the correct filename for your JS game code.
{% endhint %}

## Create New Folder\(s\) for Assets

In your code editor, create a new folder named `assets` in the same location as your HTML, CSS, and JS files. You'll use this folder to contain asset files used in your game, such as images, animated sprites, sound effects, etc.

If your game will have lots of assets, you may want to create subfolders **inside** the `assets` folder to contain specific types of assets \(to keep your files more organized\).  For example, you could create a subfolder called `images` and another subfolder called `sounds`.

Later, you'll add \(or upload\) your asset files into the `assets` folder \(or into one of its subfolders such as `images` or `sounds`\).

## HTML Template

Copy this HTML, and paste it into your `index.html` file \(replacing any other starter HTML that might already be present\):

```markup
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>My Game</title>
    <link href="style.css" rel="stylesheet" type="text/css">
  </head>
  <body>
	<div id="my-game"></div>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/phaser-ce/2.13.2/phaser.min.js"></script>
	<script src="script.js"></script>
  </body>
</html>
```

This is the basic HTML required for a Phaser CE game. All of your games will start with this HTML \(though you can also insert additional HTML to customize the game's webpage\).

Here is an explanation of the key things this HTML does: 

* **STYLESHEET:**  The `<link>` tag on line 7 loads your CSS stylesheet file named `style.css`, which can be used to style the webpage your game is embedded within.
* **GAME CANVAS CONTAINER:**  The `<div>` element on line 10 will contain your game canvas, which will literally be a `<canvas>` element that will be inserted by your Phaser game code. This `<div>` element has been given an id name of `my-game`, so your Phaser game code can identify where to insert the canvas for your game.
* **PHASER CE FRAMEWORK:**  The `<script>` tag on line 11 loads the Phaser CE game framework JS file named `phaser.min.js`. In this case, the file is being loaded remotely from a CDN \(Content Delivery Network\) using a URL. However, if necessary, this `<script>` tag can be modified to load a local copy of the Phaser CE JS file.
* **YOUR GAME CODE:**  The `<script>` tag on line 12 loads your JS file named `script.js`, which will contain your Phaser game code. You can use a different name for this file \(such as: `code.js` or `game.js`\) as long as the `<script>` tag matches the filename of your game code.

{% hint style="success" %}
**IMPORTANT:**  Be sure the `<script>` tag that loads the Phaser CE game framework \(`phaser.min.js`\) is listed **before** the `<script>` tag that loads your game code \(`script.js`\). If their order is reversed, your game won't work.
{% endhint %}

## CSS Template

A Phaser CE game does **not** require any special CSS in order for the game to work.

However, you'll add some **optional** CSS to style the `<div>` element that will contain your game canvas. Remember that this `<div>` element was given an id name of `my-game` which can be used to select this element with your CSS.

Copy this CSS, and paste it into your `style.css` file \(replacing any other starter CSS that might already be present\):

```css
/* optional CSS for game container */
#my-game {
  width: 800px;
  height: 600px;
  margin: 0 auto;
  border: 1px solid black;
}

/* optional CSS for webpage */
body {
  font-family: sans-serif;
  text-align: center;
}
```

Here is an explanation of what this CSS does:

* Lines 3 and 4 set the width and height \(in pixels\) for the `<div>` element that will contain the game canvas.  Later in your JS game code, you'll set your game canvas to these same exact dimensions. You can change these dimensions as long as the width and height listed in your CSS and your JS game code match each other.
* Line 5 sets the margins around the `<div>` element. The top and bottom margins have been set to zero. The left and right margins have been set to `auto`, which will center the game canvas horizontally on the webpage.
* Line 6 displays a border around the `<div>` element.
* Lines 11 and 12 set the `<body>` element to use a sans-serif font for all text, which will be center-aligned on the webpage.

Again, all of this CSS is **optional**. If you wanted, you could modify this CSS — or add other CSS to style additional properties for the elements on the webpage.

## JS Template

Copy this JS, and paste it into your `script.js` file \(replacing any other starter JS that might already be present\):

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

This is the core JS required in all Phaser CE games. Your game code will always start with this JS \(though you will need to add more code to actually complete your game\).

There are comments embedded in the JS to help explain the code. Here's a more detailed explanation of what this JS does:

* **PHASER GAME OBJECT:**  Line 2 creates a `Phaser.Game` object \(using a class defined in the `phaser.min.js` file\) and assigns it to a global variable named `game`. This also sets the width and height \(in pixels\) for the game canvas. In this case, the game will be 800 pixels wide and 600 pixels tall. This also specifies the id name of the `<div>` container where the game canvas will be inserted. In this case, the id name used in your HTML is `my-game`. \(If you were to change the width or height of your game canvas, just be sure to also adjust the size of `my-game` in your CSS, so they match.\)
* **GLOBAL VARIABLES:**  Line 5 is an empty placeholder where you will eventually add code to declare other global variables needed for your game. For example, you might need to declare a global variable to store the player's score.  You'll also need to declare global variables for images, sprites, sound effects, player input controls, etc. 
* **PRELOAD FUNCTION:**  Line 8 defines a function named `preload()` that will run one time when the webpage first loads \(or is refreshed\). At the moment, there are no code statements inside the curly braces of the `preload()` function. However, you will eventually add Phaser code to load your game assets into memory \(such as: images, sprites, sounds, etc.\).
* **CREATE FUNCTION:**  Line 13 defines a function named `create()` that will run one time **after** the `preload()` function has finished. At the moment, there are no code statements inside the curly braces of the `create()` function. However, you will eventually add Phaser code to create your game world by adding images, sprites, sound effects, input controls, etc.
* **UPDATE FUNCTION:**  Line 18 defines a function named `update()` that will run repeatedly in a loop **after** the `create()` function has finished running. At the moment, there are no code statements inside the curly braces of the `update()` function. However, you will eventually add Phaser code to update your game by checking for player input, checking for collisions between sprites, etc. 
* **CUSTOM FUNCTIONS:**  Line 23 is an empty placeholder where you will eventually add code to define your own custom functions needed for your game. For example, you might need to define a custom function to perform certain actions when the player's sprite collides with an enemy sprite. These custom functions will only run if and when they're specifically called within other functions \(such as the `update()` function, etc.\).

You're now ready to start adding additional code into your JS file to complete your game. Most of this additional code will be Phaser CE code.



