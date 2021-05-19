# Steps 1 - 5

## Step 1: Modify HTML and CSS

In your HTML file \(**index.html**\), add a paragraph with your name after `<div id="my-game"></div>` \(which is the container for your game\):

```markup
<p>Coded by Firstname Lastname</p>
```

**Refresh your preview of your HTML file to verify that the paragraph with your name shows up under the black box and is left-aligned on the webpage.**

In your CSS file \(**style.css**\), let's add a background color to the webpage body and let's center all the text on the webpage body.

Add this new CSS into **style.css** before `#my-game` \(which styles the `<div>` containing your game\).

```css
body {
    background: #dddddd;
    text-align: center;
}
```

**Refresh your preview of your HTML file to verify that the paragraph is center-aligned on the webpage and the webpage has a light gray background color \(but your game doesn't\).**

That's all we're going to do with the HTML and CSS files for this practice, but feel free to make other changes to the webpage \(such as: picking a different background color for the webpage, adding text above the game container, etc.\).

## Step 2: Look at Starter Phaser JS Code

Before we start coding the game, let's get oriented to the starter Phaser code already in your **code.js** file. We're just going to look at some code in this step.

**Don't** add or revise any code during this step. Just focus on understanding how the code works.

The first thing your JS code does is create a new Phaser.Game object by assigning it to a variable named `game`:

```javascript
// REMINDER: Do not copy and paste this code - it's already in your starter code

var game = new Phaser.Game(800, 600, Phaser.AUTO, 'my-game',
{ preload: preload, create: create, update: update });
```

Many of the Phaser commands that you'll use will start with `game` because this is a reference to your variable named `game` — you could use a different name for this variable if you really wanted to, but almost every example Phaser code that you'll see uses `game` \(so make your life easier by using this name\).

You will notice two numbers — 800 and 600. These represent \(in order\) the width and height \(in pixels\) of your game display. You could change these numbers for your own game, but for right now, we'll just stick with these.

Notice where it says `'my-game'` — this represents the id name of the `<div>` in your HTML file where Phaser inserts your game. You could change this id name, but you'd want to make sure the new id name matches in your HTML, CSS, and JS files.

Finally, notice that it refers to `preload`, `create`, and `update`. These are the names of 3 core Phaser functions that will be used in your game. If you look down further in your JS file, you will see these functions listed — except they are empty at the moment. You will be adding Phaser commands inside these functions to build your game:

* **PRELOAD:** The `preload()` function is used to load game assets \(such as images, sounds, etc.\) into the game's memory, so they are all ready at the same time for use in the game. The `preload()` function runs one time at the start of the game \(i.e., when the webpage loads\).
* **CREATE:** The `create()` function is used to create your game world and its user interface by adding images and sounds into the game, adding player controls, adding text, etc. The `create()` function runs one time after the `preload()` function is finished.
* **UPDATE:** The `update()` function is used to update the gameplay by checking for player input, checking for conditions or events, updating objects in the game world, etc. The `update()` function runs in a continuous loop after the `create()` function is finished. The `update()` function loops many times per second, allowing for smooth animations and responsive interactions.

Two other things to notice in your code.js template:

* There is a place near the top where you may need to declare global variables for certain objects in your game \(such as: the player, a group of enemies, the score, etc.\).
* There is a place at the bottom where you may need to create custom functions to handle certain conditions or events in the game.

## Step 3: Change Background Color of Game

By default, Phaser makes the background color of your game black. You can change the background color, or you can add images as a background for your game.

In your JS file \(**code.js**\), add this Phaser command inside `function create()` by pasting the command on a blank line between the curly braces `{ }`:

```javascript
game.stage.backgroundColor = '#6699ff';
```

Does your code look like this now? Good.

```javascript
function create() {
    game.stage.backgroundColor = '#6699ff';
}
```

**Refresh your preview of your HTML file to verify that your game now has a blue background color.**

### How do Phaser commands work?

Remember that you created a Phaser.Game object named `game` at the start of your game code. An **object** is a special type of variable that can contain a set of **properties** \(variables\) and **methods** \(functions\).

In fact, a property within an object can be another object — in other words, an object can contain other objects inside it.

Besides the main Phaser.Game object itself, there are other types of Phaser objects that you will be creating and using in your game. Each of these objects will have its own set of properties and methods \(which are defined by the Phaser JS library\).

Every Phaser command is a reference to a Phaser object property or a Phaser object method. If the command has parentheses `()`, it's a reference to a method. Otherwise, it's a reference to a property.

The [Phaser API documentation](https://photonstorm.github.io/phaser-ce/) is a reference that describes all the Phaser objects and their properties and methods.

**RESOURCE:** [W3Schools has a great explanation of JavaScript Objects](https://www.w3schools.com/js/js_objects.asp)

So let's look at this Phaser command:

```javascript
game.stage.backgroundColor = '#6699ff'; // example Phaser command
```

The first part of this Phaser command is: `game.stage`

Within your Phaser.Game object named `game`, there is a property \(a variable\) called `stage` — the Phaser JS library automatically created this property \(along with other properties and methods\) inside your Phaser.Game object when the `game` variable was created at the beginning of your **code.js** file.

Notice that a period is used to separate the name of the object and the name of the property \(or method\) within that object.

This property called `stage` is a variable representing the game display. In fact, it turns out that `stage` is also an object, meaning that it has its own set of properties \(variables\) and methods \(functions\).

Within the `stage` object, there is a property called `backgroundColor` which is exactly what it sounds like: it determines the color of the game display background. When a Phaser.Game object is first created, this `backgroundColor` property within the `stage` object is set to a value of black.

So `game.stage.backgroundColor` is a reference to the background color of the stage within the game. The last part of the command uses an equals sign to change the value of this property to blue \(`#6699ff` is a CSS hex color code for blue\).

That's how Phaser commands work, in a nutshell.

## Step 4: Add Emoji Sprite Using Image

Let's add an image to your game. Inside your **assets** folder is an image file called **hello-sprite.png** that looks like this:

![](../../.gitbook/assets/hello-sprite.png)

What looks like 6 separate images is actually one combined image. PNG image files can have transparent backgrounds \(which this image has\).

If you view this image in an image editor \(such as: Pixlr, etc.\), it will look like it has a checkboard background:

![](../../.gitbook/assets/hello-sprite-alpha.png)

The image editor displays the transparent areas as a checkboard pattern to make it clear \(get it? _clear_\) what parts of the image are transparent. When you use this image in your game, you won't see any checkerboard pattern.

You're going to add this image to your game as something called a **spritesheet**. A spritesheet is an image that will be subdivided into a set of smaller images.

A typical use for a spritesheet is to contain a set of animation frames for an object in your game \(such as: player's character, etc.\). Animations work by showing a sequence of frames — one at a time — in rapid succession to create the illusion of something moving or changing.

A **sprite** is a game object \(such as: the player's character, an enemy, etc.\) that uses a spritesheet. At any given moment during gameplay, a sprite only displays one possible frame from its spritesheet. By rapidly changing which frame is displayed, the game can animate the sprite.

Every animation frame in a spritesheet has to have the same rectangular size. In our case, our frames happen to be squares that are 64 pixels in width and 64 pixels in height. Here's our spritesheet image with the frames highlighted, so you can see how it will be sliced up into smaller images:

![](../../.gitbook/assets/hello-sprite-outline.png)

Technically, this particular spritesheet is _not_ really an animation. Instead, it just shows the 6 possible emojis for our matching game. Combining these 6 images into a single spritesheet image \(instead of 6 separate image files\) just makes it easier to use in this particular game \(as you'll see later in Step 5\).

Here's a spritesheet for a different game that does actually show animation frames:

![](../../.gitbook/assets/space-dude-sprite.png)

This spritesheet contains 9 animation frames: the first four frames show a little dude running to the left \(_imagine these four frames playing over and over again in a loop_\), the fifth frame shows him \(or her?\) standing still, and the last four frames show the little dude running to the right. You'll meet this little dude again in Practice 3.

You will need to declare \(i.e., create\) a global variable to represent your sprite. Add this JavaScript statement near the top of your code \(_look for the comment line that mentions global variables_\).

```javascript
var hello1;
```

This statement creates a new variable named `hello1`. You get to decide the names of variables, as long as each variable has a unique name \(and as long as the variable name is _not_ a [reserved word in the JavaScript language](https://www.w3schools.com/js/js_reserved.asp)\).

You're going to name this variable `hello1` because eventually you'll have 3 sprites in your game \(`hello1`, `hello2`, `hello3`\). You could call them `Moe`, `Larry`, and `Curly` if you really wanted — as long as each variable has a unique name.

**RESOURCE:** [W3Schools has a JavaScript tutorial on Variables](https://www.w3schools.com/js/js_variables.asp)

Before you can add a sprite to your game, you have to load its spritesheet into the game's memory. Add this Phaser command inside `function preload()` by pasting the command on a blank line between the curly braces `{ }`:

```javascript
game.load.spritesheet('hello', 'assets/hello-sprite.png', 64, 64);
```

Does your code look like this now? Good — just checking.

```javascript
function preload() {
    game.load.spritesheet('hello', 'assets/hello-sprite.png', 64, 64);
}
```

You can see the first part of the Phaser command indicates that you're loading a spritesheet into your game. Let's take a look at what's inside the parentheses:

* `'hello'` represents an asset key — a key is sort of like a variable name. You decide what name to use for the key. Similar to variable names, each key should have a unique name, and the name cannot contain any spaces. In other Phaser commands, if you use this specific key name, Phaser will know that you are referring to this particular spritesheet.
* `'assets/hello-sprite.png'` represents the folder path and filename of the spritesheet image to load.
* `64, 64` represent \(in order\) the width and height \(in pixels\) of each frame in this particular spritesheet. Phaser will use these measurements to divide the spritesheet into a set of individual frames.

Now that the spritesheet is loaded, the next step is to actually add your first sprite to the game world.

Add this Phaser command inside `function create()` by pasting the command on a new line after the command to change the game's background color:

```javascript
hello1 = game.add.sprite(400, 300, 'hello');
```

This command adds a sprite to the game and assigns that sprite to the `hello1` variable. So now, when you refer to `hello1` in your code, you are referring to this sprite.

Let's look at what's inside the parentheses:

* `400, 300` represent the x and y coordinates \(in order\) of the pixel position where the sprite will be added to the game. The top-left corner of your game is `0, 0`. The values for the x-position increase from left to right. Since your game was set as 800 pixels wide, the x-position of the right edge of your game is 799 \(because the first pixel is actually numbered as 0\). The values for the y-position increase from top to bottom. Since your game was set as 600 pixels high, the y-position of the bottom edge of your game is 599. So `400, 300` is basically the center of your game.
* `'hello'` is the asset key name of the spritesheet to use for this sprite.

**Refresh your HTML preview to verify that your game now has the emoji sprite inserted.**

You will notice a couple of things:

1. Instead of seeing all 6 emoji frames, the sprite only shows one frame — this is normal and exactly what we want. Sprites only show one frame at any given time, and a sprite will show the first frame by default until you tell it to either show a different frame or play an animation sequence.
2. The sprite does _not_ look centered. Instead, the top-left corner of the sprite is positioned at the game's center \(`400, 300`\). By default, Phaser positions objects using their top-left corner as the "anchor" point. Sometimes this is exactly what you want. However, for some game objects — like a player's character, etc. — it will make more sense to use the center of the object \(or some other point\) as its "anchor" point for positioning in the game.

Add this Phaser command inside `function create()` on a new line after the command that added the `hello1` sprite:

```javascript
hello1.anchor.set(0.5, 0.5);
```

This command will change the sprite's anchor point for positioning to be the center of the sprite \(`0.5, 0.5` means set the anchor to half-way across its width and half-way down its height\).

**Refresh your HTML preview to verify that the sprite is now centered in the game.**

In fact, rather than you needing to figure out the x and y values for the center of your game, you can use a built-in Phaser property that calculates these values automatically.

Modify your existing command that adds the sprite, so the command looks like this instead:

```javascript
hello1 = game.add.sprite(game.world.centerX, game.world.centerY, 'hello');
```

**Refresh your HTML preview to verify that the sprite is still centered in the game.**

## Step 5: Add Player Input

A game needs to provide a way for the player to interact with the game. Phaser supports various types of player input: keyboard input, mouse input, multi-point touch input, and even gamepad input.

You're going to add a keyboard input. Phaser allows you to designate specific keys on the keyboard as inputs. In this game, the player will use the spacebar key to "spin" the emoji sprite, so it randomly switches between the different emoji frames.

You need to declare a global variable for each input used in your game, so create another global variable called `spacebar`.

You already have a line of code that added the `hello1` global variable, so you have a couple of different options for adding a new variable:

\(1\) You could add a new `var` statement for the new variable, so your code looks like this:

```javascript
var hello1;
var spacebar;
```

**OR**

\(2\) You could modify the existing `var` statement to include the new variable \(use a comma to separate the names\), so your code looks like this:

```javascript
var hello1, spacebar;
```

Just choose one of the options above. In later steps, you'll need to add even more global variables, so keep these two options in mind.

Add this Phaser command inside `function create()` on a new line after the command that sets the anchor for the `hello1` sprite:

```javascript
spacebar = game.input.keyboard.addKey(Phaser.KeyCode.SPACEBAR);
```

This command makes a specific key on the keyboard into an input and assigns it to your variable. You just have to provide the Phaser.KeyCode for the specific key. This reference lists [all the available Phaser keycodes](https://photonstorm.github.io/phaser-ce/Phaser.KeyCode.html).

Next we need to make the game actually do something when the player presses the spacebar.

Phaser has several properties for detecting input on keys. Here are four properties for a key that will have a value of either true or false:

* `isDown` will detect if the key is currently pressed down — this property will remain true for as long as the player continues to hold the key down
* `isUp` will detect if the key is currently up \(i.e., not being pressed\) — this property will remain true for as long as the player doesn't press the key
* `justDown` will detect if the key was just pressed down during the current game loop \(so you can detect exactly when the key is pressed down\) — this property is only true during the specific game loop when the key is first pressed down — after that loop, it becomes false, even if the player keeps pressing the key
* `justUp` will detect if the key was just released during the current game loop \(so you can detect exactly when the key is released\) — this property is only true during the specific game loop when the key is first released — after that loop, it becomes false, even if the player still isn't pressing the key

Let's detect when the spacebar key is being pressed down. If that's true, we'll change the sprite to a random frame \(one of the 6 possible emojis\).

Add this Phaser code inside `function update()` by pasting the code on a blank line between the curly braces `{ }`:

```javascript
    if (spacebar.isDown) {
        hello1.frame = Math.floor(Math.random() * 6);
    }
```

This `if` statement will detect whether the spacebar is currently pressed down. If this condition is true, then it will change the sprite to a random frame. Otherwise, if this condition is false \(i.e., when the spacebar is not being pressed\), it won't change the sprite frame.

Here's a few things to note about this code:

* `if` statements are commonly used in computer programs to make decisions about what actions to perform \(or not perform\) based on specific conditions being true or false. You will need to understand how these work.
* Sprite frames are referenced by number, with the first frame numbered as 0, the second frame numbered as 1, the third frame numbered as 2, etc. The emoji spritesheet contains 6 frames, which Phaser numbers as 0 to 5.
* The statement `Math.floor(Math.random() * 6)` generates a random whole number between 0 and 5 \(i.e., 6 possibilities\). Random numbers are commonly used in games — they are very helpful for adding some variation and unpredictability to the gameplay.

**Refresh your HTML preview to verify that if you press the spacebar, the sprite will randomly change to a different emoji.**

If you keep holding the spacebar down, the sprite will keep changing randomly — it will change every time the `update()` function completes a loop. \(This should give you a good idea of how fast one game loop is.\) If you release the spacebar, the sprite should stop changing.

**RESOURCE:** [W3Schools has a JavaScript tutorial on If-Else Conditional Statements](https://www.w3schools.com/js/js_if_else.asp)

**RESOURCE:** [W3Schools has a JavaScript tutorial on Random Numbers](https://www.w3schools.com/js/js_random.asp)

## Steps 6-10 continue on next page

