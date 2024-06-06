# Final Development Update

The development period for Labyrinth Legends is now officially over!
Here is a run-down of the game in it's current (and final) state.

## Menus

### Main Menu
On starting the game, the player is met with the Main Menu, and from here it's possible to either start the game or navigate further into one of the other menus.

![Main Menu](/Labyrinth-Legends/resources/showcase/mainmenu.png)

### Options
In the Options-menu, it is possible to change the game volume. The volume-state is stored in the PlayerPrefs file, meaning that it will persist over game-sessions.
In hindsight, more options could be added - such as remappable controls, screen resolution, clearing of high scores and seperate volume sliders for music and sound effects. 

![Options Menu](/Labyrinth-Legends/resources/showcase/options.png)

### Credits
The Credits-menu simply lists the developer of the game, along with assets and tutorials used to create the game. The animation is made using the Animator component in the Unity Editor, by manipulating the transform Y property of the GameObject containing the text over a specified period of time.

![Credits Menu](/Labyrinth-Legends/resources/showcase/credits.png)

### High Score
This menu shows the current high scores achieved in the current local game install. These values are stored as a List in the PlayerPrefs file, and are limited to store at most the 10 best scores.

![High Score Menu](/Labyrinth-Legends/resources/showcase/highscore.png)

## Game

The purpose of the game is to navigate (using either a keyboard or the Joystick and the green button on the VIA Arcade machine) through (currently) 3 levels while collecting as many gems as possible. Throughout these levels, the player will encounter enemies - and has to decide whether to attack them for extra points (but running the risk of dying, and having to restart) or to avoid them.
A level is completed when the player reaches the chest - and the player is then presented with a choice of whether to continue or to exit to the Main Menu.
If time had allowed it, more levels and features could have been added to the game, such as for example a stamina system and/or the addition of ranged attacks and other different kinds of AI packagesfor the enemies.

![Level in progress](/Labyrinth-Legends/resources/showcase/gameinprogress.png)

When the game is completed, the player is presented with a screen allowing them to enter their name - and if their finishing score is amongst the 10 highest - it will be shown on the High Scores menu.

![Game Finished Screen](/Labyrinth-Legends/resources/showcase/overscreen.png)