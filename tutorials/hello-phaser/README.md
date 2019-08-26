# A. Hello Phaser

{% hint style="danger" %}
**UPDATE IN PROGRESS:** This new code guidebook will have revised versions of the Phaser tutorials in the previous guidebook. In the meantime, you can still access the previous Phaser tutorials for creating example games:

* [Phaser Practice 1:  Matching Game \(Emoji Match\)](https://docs.idew.org/video-game/project-outline/1-5-phaser-practice-1-matching-game)
* [Phaser Practice 2:  Top-Down Game \(Asteroids\)](https://docs.idew.org/video-game/project-outline/1-6-phaser-practice-2-top-down-game)
* [Phaser Practice 3:  Side-Scrolling Game \(Platformer\)](https://docs.idew.org/video-game/project-outline/1-7-phaser-practice-3-side-scrolling-game)
{% endhint %}

In this first tutorial, you'll code a "Hello World" game that displays the Phaser logo and changes the game's background color when the spacebar is pressed.

This won't be a true game \(because it lacks an objective, rules, challenge, etc.\). However, it will introduce you to coding with the Phaser CE game framework.

## Tutorial Goals  <a id="tutorial-goals"></a>

The goals of this tutorial are to help you:

* Understand the basic code structure of a Phaser CE game
* Code a Hello World game with a simple player interaction

## What is a Hello World program? <a id="what-is-a-hello-world-app"></a>

When learning a new programming language, the first step that many people take is to create what is called a ["Hello World"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) program. Traditionally, this program simply displays the text "Hello World" on the screen and only requires a few lines of code. The purpose is to demonstrate that you can create a simple yet functional program in the new coding language. It's a first step before creating more complex programs with the new language.

A Phaser game can display text, so we could create a traditional "Hello World" message on the game screen. However, instead, we'll display an image on the screen, since video games typically use lots of images. In addition, we'll add the ability to detect keyboard input, since video games are centered around player interaction.

