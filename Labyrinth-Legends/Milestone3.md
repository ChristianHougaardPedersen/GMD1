# Milestone 3 - AI, Audio and final touches 

This developer update will describe the third milestone in the development of Labyrinth Legends.

## Goals

The main goals for this milestone is:
- To add AI to the enemies, in order to add challenge to the game by having them move around the levels.
- To implement enemies to the game, for the player to either avoid or attack (for extra points)
- To introduce audio elements to the game, such as ambient background music, as well as sound effects when collecting gems, attacking and dying.
- Add menus to the game in the form of:
   - Main Menu
   - Options Menu
   - Credits Screen
   - High Scores Screen
- Add additional levels to the game, and the functionality to proceed to the next level upon completion of one.

## Work Done

### Enemy AI

In order to make the enemies move around, inspiration was found in the Course Materials where some example AI packages were uploaded. Expanding upon that, I found a [YouTube video](https://www.youtube.com/watch?v=l7VyxIzAIAc) covering the topic as well.
I decided going for patrolling enemies, as in that way the enemies can "guard" gems and add a risk/reward element to the game.
The AI is implemented in the EnemyPatrol script, and works in such a way that the script takes a variable number of "patrol points", and the Co-Routine then makes the enemy navigate to each one of them in a loop, for as long as it is still alive.
When the enemy is killed by the Player, an event is sent from the EnemyController, which is subscribed to by the EnemyPatrol script - and on recieving this, the _isAlive boolean is set to false, making the CoRoutine stop.

![EnemyPatrolling Screenshot](/Labyrinth-Legends/resources/EnemyPatrolling.png)

### Audio

The audio in the game is controlled from the AudioManager-script, which is implemented as a Singleton and has 2 AudioSources associated with it. The first AudioSource is used to play the background music on a loop, while the second one is used to play sound effects when the corresponding method is called from another script.
![AudioManager Screenshot](/Labyrinth-Legends/resources/AudioManager.png)

### UI

In order to streamline the switching between scenes in the game, a LevelManager-singleton is introduces - with the purpose of handling the setup associated with switching between scenes, such as resetting health and selecting the scene to switch to.
![LevelManager Screenshot](/Labyrinth-Legends/resources/LevelManager.png)

The Main Menu and options menu share a Scene, with the options menu being a panel that is activated when clicking the Options-button.
Currently, the only option available is to change the volume in the game.
The volume is saved in the PlayerPrefs-file, in order to make it persist between play sessions.

The Credits and HighScores menu options each open a new Scene, with the Credits-scene showing a "movie-like" representation of the credits for the game.

The HighScores Scene lists the Top-10 high scores achived in the game. I struggled quite a bit with trying to figure out how to create a table-like structure for the layout in the Unity-Editor, but I am quite satisfied with the end result.
The High-Scores are saved and loaded from the PlayerPrefs file, by serializing a List of the Top-10 scores as JSON and then deserializing them to individual High Score Entries, each containing a player name and the achieved score.
![HighScore Manager Screenshot](/Labyrinth-Legends/resources/HighScoreManager.png).

When completing the game, the GameEndScene is triggered, on which the score achieved is shown as well as a Player Name field, where you cycle through characters in order to enter your High Score.
![GameEndScreen gif](/Labyrinth-Legends/resources/GameEndScreen.gif)

### "Presentation"

Shown below is a short video presentation of the current progress.
The different new menus can be seen in action, as well as a quick run-through of one of the new levels.

![Milestone 3 Video](/Labyrinth-Legends/resources/milestone3.gif)