# A-6 Add Input to Game

Finally, let's add a way for a player to interact with the game by pressing a key.

Phaser CE supports the ability to detect input through a keyboard, mouse, touch \(for mobile devices\), and gamepads.

## Declare Variable for Input Key

declare global variable to represent the input key

```javascript
var spacebar;
```

## Add Input Key to Game

add the input key in the create\(\) function

```javascript
  spacebar = game.input.keyboard.addKey(Phaser.KeyCode.SPACEBAR);
```

## Check Input Key During Gameplay

check input key in update\(\) function using if statement to perform certain actions when the key is pressed

```javascript
  if (spacebar.justDown) {
    game.stage.backgroundColor = Phaser.Color.getRandomColor();
  }
```

## Preview Game

Preview the game in your code editor. Depending on your code editor, you might need to refresh its preview pane. If necessary, open the preview in a new tab or window to view it in fullscreen.

![](../../.gitbook/assets/hello-phaser-final-preview.jpg)

