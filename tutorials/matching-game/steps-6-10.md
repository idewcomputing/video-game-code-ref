# Steps 6 - 10

## Step 6: Add Sound Effect

Now that you've added a way for the player to interact with the game, let's add a sound effect as feedback to the player. We'll play a "spinning" sound as the emoji randomly changes.

Adding a sound is similar to adding a sprite:

* you declare a global variable for it
* then you preload it
* then you add it to the game

Add a global variable named `spinSound` to your code.

Within your `preload()` function, add this Phaser command:

```javascript
game.load.audio('spin', 'assets/spinner.mp3');
```

You can see the first part of the Phaser command indicates that you're loading audio into your game. Let's take a look at what's inside the parentheses:

* `'spin'` represents the asset key for this sound. Again, the key is a reference, similar to a variable name, and you get to decide the name for the key.
* `'assets/spinner.mp3'` represents the folder path and filename of the sound file that will be loaded. You can only use the following types of sound files in your game: wav, mp3, ogg

Add this Phaser command inside `function create()` to add the sound to the game:

```javascript
spinSound = game.add.audio('spin', 0.3);
```

This command adds the sound to the game and assigns that sound to the `spinSound` variable.

* `spin` is the asset key for the sound file to use
* `0.3` represents the volume for this sound, which can be a value between 0 to 1 \(with 1 being the file's maximum volume\).

Be aware that the sound won't actually play until we use a command telling it to start playing.

By default, when you do play a sound, the sound will play one time and then stop. However, we want our spinning sound to keep playing over and over, for as long as the spacebar is held down.

So add this Phaser command after the command that added the audio:

```javascript
spinSound.loop = true;
```

This will make the sound keep playing in a loop once it's started. The sound will keep looping until we specifically tell the sound to stop playing.

For your game, your code will start playing the sound when the spacebar is first pressed down. The sound will keep playing on a loop as long as the spacebar is still being held down. Then your code will stop playing the sound as soon as the spacebar is released.

Modify your existing code inside the `update()` function, so it looks like this:

```javascript
    if (spacebar.justDown) {
        spinSound.play();
    }
    else if (spacebar.isDown) {
        hello1.frame = Math.floor(Math.random() * 6);
    }
    else if (spacebar.justUp) {
        spinSound.stop();
    }
```

Notice that we're using a series of [if-else conditional statements](https://www.w3schools.com/js/js_if_else.asp). The game will check these conditions in the order listed.

The game will check to see whether the first condition \(`spacebar.justDown`\) is true. If that condition is true, it will start playing the sound \(which will keep playing over and over since we set it to loop\) and then skip the other two conditions.

Otherwise, if that first condition is false, then it will check the second condition \(`spacebar.isDown`\). If that condition is true, it will change the sprite to a random frame and then skip the last condition.

Otherwise, if that second condition is false, then it will check the third condition \(`spacebar.justUp`\). If that condition is true, it will stop playing the sound.

**Refresh your HTML preview to verify that if you hold down the spacebar, the spinning sound will play — but as soon as you release the spacebar, the sound will stop.**

## Step 7: Add Text to Game

Eventually, this game will have three emoji sprites that the player randomly spins, and the game will award score points for for matching emojis and subtract points if there's no match.

The score will displayed as text in the game display. So let's add this text that will eventually display the score — but in the meantime, we'll just have the text display instructions for how to spin the emojis. Later, we'll update this text to display the score.

Add a global variable named `scoreText` to your code.

Add this Phaser command inside `function create()` to add text to the game:

```javascript
scoreText = game.add.text(game.world.centerX, game.world.centerY + 80,
    'Use Spacebar to Spin',
    { font: 'Arial', fontSize: '20px', fontStyle: 'bold', fill: '#ffffff' });
```

This command adds the text and assigns it to the `scoreText` variable.

Let's take a look at what's inside the parentheses of this command:

* First you provide the x and y coordinates \(in order\) of the pixel position where the text should be added to the game.
* Then you can provide the actual text to display by listing it within quotes: `'Use Spacebar to Spin'`
* Then within a set of curly braces `{ }`, you have the option of listing style properties for the text. This example lists a font, a font size, a font style, and a fill \(i.e., text color, which will be a CSS hex color code\). You don't have to list all of these, but usually you'll want to provide the font, the font size, and the fill color. The Phaser API reference identifies [all the style properties for text](https://photonstorm.github.io/phaser-ce/Phaser.Text.html).

**Refresh your HTML preview to verify that the text appears in the game.**

Just like when we first added the sprite, the text is _not_ centered because its top-left corner represents its x and y position. Let's fix that by setting a different "anchor" point for the positioning of the text.

Add a command to change the text's anchor point to be the center of the text. \(Hint: How do you do this previously for the `hello1` sprite?\)

**Refresh your HTML preview to verify that the text is now centered horizontally below the emoji sprite.**

## Step 8: Add Other Emoji Sprites

Now you're going to add the other two emojis to your game, so you can start building the "matching" part of the game.

In your `create()` function, modify the existing command that adds the `hello1` sprite, so it looks like this instead:

```javascript
hello1 = game.add.sprite(game.world.centerX - 100, game.world.centerY, 'hello');
```

**Refresh your HTML preview to verify that the sprite is now shifted slightly to the left of the game's center.**

Now you'll add two more emoji sprites. These will use the same spritesheet as the first emoji sprite. Your code only needs to load this spritesheet one time — you'll just reuse the same spritesheet by referring to its asset key when you add each of the other sprites.

Create two more global variables called `hello2` and `hello3`.

Within your `create()` function, add the `hello2` sprite to the center of the game, and add the `hello3` sprite 100 pixels to the right of the game's center. Remember that both of these new sprites will just reuse the existing `'hello'` spritesheet.

Be sure to set the anchor point for each new sprite, similar to what you did for the `hello1` sprite.

**Refresh your HTML preview to verify that you have 3 emoji sprites that are equally spaced in a row across the center of your game.**

If you press down the spacebar, only the first sprite \(which is `hello1`\) will randomly change, while the other two sprites stay the same. You'll fix this in the next step.

## Step 9: Add Custom Function to Check for Matches

Now that you have all 3 emoji sprites added, add code within your `update()` function to make `hello2` and `hello3` also change to a random frame whenever the spacebar is down.

**Refresh your HTML preview to verify that each of the 3 emoji sprites changes randomly when the spacebar is pressed — and they keep changing randomly as long the spacebar is held down.**

We want to add a score to the game, so the player will be awarded points if there are matching emojis after a spin.

Create a global variable named `score` and assign it an initial value of zero for the start of the game:

```javascript
var score = 0;
```

You'll use `score` to actually keep track of the numerical score during the game, and then use `scoreText` to display the `score` on the game screen.

Now that you have a `score` variable, you need to add code to check for emoji matches after each spin and then update the score. You're going to add this code inside your own custom function \(so you can practice making a new function\).

As you've seen, a **function** contains a set of related code statements that perform a specific task or function, such as preloading game assets, etc.

Add the following JavaScript code to the very bottom of your **code.js** file \(after the `update()` function\):

```javascript
function checkMatch() {

}
```

This creates a new function in your JavaScript. Right now, this function is empty — it has no code between its curly braces `{ }` — but you'll be adding code inside the function in just a little bit.

As you can see, `checkMatch` is the name of the function. Just like variable names, you get to decide the name of the function, as long as every function in your code has a unique name. Functions always have a set of parentheses `()` at the end of their name. Sometimes there are variable names called **parameters** listed inside the parentheses — but we don't need parameters for this particular function.

**RESOURCE:** [W3Schools has a JavaScript tutorial on Functions](https://www.w3schools.com/js/js_functions.asp)

Let's figure out the code to add inside the `checkMatch()` function. As soon as the spacebar is released, we want to check to see if any of the emoji sprites match each other.

The easiest way to check for matches is to compare the frame numbers of the sprites. If they currently have the same frame number, that means they are displaying the same exact emoji.

* We want to first check to see if all 3 sprites match. If they do, we'll add 100 to the score as a reward. In JavaScript \(like other programming languages\), you can only compare two variables at a time, so we'll need to combine multiple comparisons into one conditional statement. So if `hello1` and `hello2` have the same frame AND `hello2` and `hello3` have the same frame, then all 3 match. \(We don't even need to check `hello1` vs. `hello3` because they will logically match if the other two comparisons were true.\)
* Otherwise, we want to check to see if any 2 of the sprites match. If they do, we'll add 20 to the score as a reward. There are three possibilities for a double match: `hello1` and `hello2` match OR `hello2` and `hello3` match OR `hello1` and `hello3` match. Again, we'll combinine these multiple comparisons into one conditional statement.
* Otherwise, if both of these checks were false, it means none of the sprites match \(all three are different emojis\). In that case, we'll subtract 10 from the score as a punishment.

Lastly, regardless of which of these is true \(all 3 match, any 2 match, or none match\), we will need to update `scoreText` to display the new score.

Add this code inside `function checkMatch()` by pasting it between the curly braces `{ }`:

```javascript
    if (hello1.frame == hello2.frame && hello2.frame == hello3.frame) {
        // all 3 match
        score = score + 100;
    }
    else if (hello1.frame == hello2.frame || hello2.frame == hello3.frame
    || hello1.frame == hello3.frame) {
        // any 2 match
        score = score + 20;
    }
    else {
        // none match
        score = score - 10;
    }

    scoreText.text = score;
```

Let's examine this code:

* When you are [comparing two variables](https://www.w3schools.com/js/js_comparisons.asp) to see if they are equivalent to each other, you have to use **double equals** signs `==`. This is because JavaScript \(like most other programming languages\) uses a single equals sign `=` to assign or change the value of a variable.
* `&&` represents AND.  By using `&&` to combine multiple comparisons into one condition, the condition will be true only if every comparison in the set is true.
* `||` represents OR. By using `||` to list multiple comparisons within one condition, the condition will be true if any one \(or more\) of the comparisons is true \(even if the others are false\).
  * **Hint:** You can type `|` by pressing shift-backslash on your keyboard
* Notice we first checked for a triple match, and then checked for a double match. If we reversed the order of these checks, the code would treat 3 matching emojis as a double match. \(Do you understand why?\)
* You can change the value of a variable, such as `score`, by using a **single equals** sign `=`. You can even refer to the previous value of the variable. In our case, the code assigns a new value to `score` by taking its previous value \(which is saved as `score`\) and then adding or subtracting a number.
* You change the text being displayed by assigning a new value to the `text` property of your text variable. In our case, we just want to display a number \(the player's `score`\). If you wanted to display some actual text, you would list it inside quotes: `scoreText.text = 'Triple Match!';`

The `checkMatch()` function won't actually run until and unless we tell the game to do so. You run a function by "calling it" — which simply means listing its name with a set of parentheses. \(If the function happened to require parameters, then you'd also list parameters within the parentheses — but your function doesn't require these.\)

Since we want to perform the check for matches as soon as the emojis stop changing, add this line of code within your `update()` function, so that it will call your custom function when the spacebar has just been released:

```javascript
checkMatch();
```

The game will recognize that this is the name of one of your custom functions — so it will go and perform all the code listed inside that custom function, and then it will return back to where it was.

**Refresh your HTML preview and play the game to verify that it correctly identifies when a match occurs and correctly awards points based on a triple match, double match, or no match.**

Your game should be functioning correctly at this point. The score should be changing, though it may be a little challenging to determine if it is changing accurately. We'll fix this in the last step, so the game provides clear feedback to the player.

## Step 10: Add Improvements to Game

For this last step, you'll add some things to improve the game. You'll make it easier for the player to understand what's happening and also make the game a little more fun.

As some visual feedback to the player, let's change the game's background color to a random color after every spin. It helps make it clear when a "spin" has ended — plus it adds another interesting random element to the game.

Add this Phaser command within your `update()` function, so that it will occur when the spacebar has just been released:

```javascript
game.stage.backgroundColor = Phaser.Color.getRandomColor();
```

**Refresh your HTML preview to play the game and verify that the game background changes to a random color after each spin.**

You will notice that the white color of the `scoreText` can be hard to read when the background color randomly changes to a light color. To help fix that, let's add a shadow behind the text to make it easier to read.

Add this Phaser command in your `create()` function after the command that added `scoreText` to the game:

```javascript
scoreText.setShadow(1, 1, '#000000', 2);
```

This will add a small dark shadow behind the white text, making it a little easier to read on light-colored backgrounds. If you want to learn more about the settings inside the parentheses, here is the Phaser API reference for [setShadow](https://photonstorm.github.io/phaser-ce/Phaser.Text.html#setShadow), which explains it in detail.

**Refresh your HTML preview to verify that the text shadow is visible.**

Okay, let's add sound effects for a triple match and a double match.

Create two more global variables called `match2Sound` and `match3Sound`.

Within your `preload()` function, load the sound files in your assets folder called **coin.wav** and **power-up.wav**. Be sure to assign a unique asset key name to each sound \(use something that makes sense to you\).

Within your `create()` function, add the sounds to your game. Use **coin.wav** for `match2Sound`, and use **power-up.wav** for `match3Sound`. Set a volume for each sound \(which you can modify later after testing them out in the game\). Since we only want these sounds to play one time whenever we do play them, you don't need to adjust their `loop` property \(it will be set to `false` by default\).

Within your `checkMatch()` function, add a command to play `match2Sound` when a double match occurs, and add another command to play `match3Sound` when a triple match occurs.

**Refresh your HTML preview to play the game and verify that the correct sound plays whenever a double match or triple match occurs \(and no sound plays if there's no match\).**

Your final addition to the game will be some text feedback after each spin to confirm whether a triple match, double match, or no match occurred.

Create a global variable called `matchText`.

Within your `create()` function, add `matchText` to the game by positioning it 120 pixels below the center of the game. Set the text to read `Match 2 or 3 to Win`, and use the same font styling as you did for `scoreText`.

Add a command to change the `matchText` anchor point to be the center of the text.

Add a command to add a text shadow to `matchText` \(use the same shadow settings as you did for `scoreText`\).

Within your `update()` function, add a command to do the following:

* When the spacebar is first pressed down, clear out the text in `matchText`. You do this by assigning an empty string \(quotes with nothing inside\) to its `text` property, like this:

  ```javascript
  matchText.text = '';
  ```

Within your `checkMatch()` function, add commands to do the following:

* When a double match occurs, change `matchText` to read `Match Two +20`, and change its text color to green \(`#00ff00`\) by changing its `fill` property, like this:

  ```javascript
  matchText.fill = '#00ff00';
  ```

* When a triple match occurs, change `matchText` to read `Match Three +100`, and change its text color to green.
* When no match occurs, change `matchText` to read `No Match -10`, and change its text color to red \(`#ff0000`\).

**Refresh your HTML preview to play the game and verify that the correct feedback text appears after each spin.**

What else do you think could be added or changed to improve this game? Why?

Congratulations, you've completed your first practice game! Hopefully, the Phaser commands made sense — you'll get the chance to use them again in the next practice game.

