# A-2 Add HTML

add starter HTML code for Phaser game

### Add HTML

Copy-and-paste this HTML markup into your `index.html` file \(replacing any starter code that might be present\):

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

This is the basic HTML required to create a Phaser game on a webpage. Here are the key things this HTML does: 

* The `<link>` tag on line 7 loads your CSS stylesheet file named `style.css`, which can be used to style the webpage that your game is embedded within.
* The `<div>` element on line 10 will contain your game canvas, which will literally be a `<canvas>` element that will be inserted by your Phaser game code. This `<div>` tag has been assigned an id named `my-game`, so your Phaser game code can identify where to insert the canvas for your game.
* The `<script>` tag on line 11 loads the Phaser CE game framework JS file named `phaser.min.js`. In this case, the file is being loaded remotely from a CDN \(Content Delivery Network\) using a URL. However, if necessary, this `<script>` tag can be modified to load a local copy of the Phaser CE JS file.
* The `<script>` tag on line 12 loads your JS file named `script.js`, which will contain your Phaser game code. You can use a different name for this file \(such as: `code.js` or `game.js`\) as long as the `<script>` tag matches the filename of your game code.

{% hint style="success" %}
**IMPORTANT:**  The `<script>` tag that loads the Phaser game framework \(`phaser.min.js`\) must be listed **before** the `<script>` tag that loads your game code \(`script.js`\). Otherwise, if their order is reversed, your game won't work.
{% endhint %}

### Add Copy of Phaser JS

In your code editor, add \(or upload\) a copy of the Phaser CE game framework named `phaser.min.js` in the same location as your HTML, CSS, and JS files.

