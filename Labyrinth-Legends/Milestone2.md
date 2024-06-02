# Milestone 2 - Animations, Extension and Enemies 

This developer update will describe the second milestone in the development of Labyrinth Legends.

## Goals
The main goal of this milestone is to extend the already implemented functionality of the game, as well as introduce Enemies as a factor in the game as well.

The main goals for this milestone is:
- To implement different types of collectibles, each giving a different amount of points when collected.
- To implement enemies to the game, for the player to either avoid or attack (for extra points)
    - As a sub-goal of this, the player character is going to have a pool of health available.
- Animations (and "final" sprite-design for the player character, enemies and collectibles)

## Work Done
As the previous milestone served primarily as a proof of concept, quite a lot has changed between that and this, the newest iteration of Labyrinth Legends!

### Resource Gathering
Firstly, all assets has been changed to their final versions. As I am by no means a designer by any means, I took to the internet to find images that would be suitable for the game.

The player and enemy sprite-sheets were created in the online-tool [Universal LPC Spritesheet Character Generator](https://sanderfrenken.github.io/Universal-LPC-Spritesheet-Character-Generator/) created by GitHub user Sander Frenken.

![Player Character Spritesheet - Cropped](/Labyrinth-Legends/resources/Player_SpriteSheet_Cropped.png)
![Enemy Character Spritesheet - Cropped](/Labyrinth-Legends/resources/SkeletonUnarmed_SpriteSheet_Cropped.png)

Other than the sprites for the characters, i also wanted nicer tilesets for my dungeons, which i found on [itch.io](https://pixel-poem.itch.io/free-rpg-tileset) and also sliced using the same method.

![Dungeon Tilemap](/Labyrinth-Legends/resources/Dungeon_24x24.png)
![Decorations Tilemap](/Labyrinth-Legends/resources/decor.png)

As shown in the images above, each of these contains multiple images and thus needed to be cropped. At first, i tried creating a python application for slicing the pictures, but with little luck as i struggled getting the exact dimensions right.
After a bit of searching, I found [this tutorial](https://christopherhilton88.medium.com/how-to-slice-up-a-spritesheet-in-unity-7caf262acad8) explaining how to do sprite slicing in the Unity Editor, which was a much easier process than i had feared.

### Animation

Using the Unity Editor, animation files were created from the character sprites, and these were implemented using the Animator component, which uses a State Machine pattern to switch between animations:

![Animations for the player character](/Labyrinth-Legends/resources/PlayerAnimStateMachine.png)

In both the Player Move and Player Attack Sub-State Machines, a BlendTree was created, meaning that depending on the X and Y inputs given (between -1 and 1), the animations will blend together.

These State Machines are controlled by the PlayerAnimationController which, other than animating based on coordinates, also acts as a listener for the HealthController component, and triggers the death-animation when the Players health reaches 0 as well as triggers the attack animation when called from the PlayerInputController. 

### Enemies

For now, enemies do not move around the level - but the Enemy-prefab has an EnemyController script attached, which currently contains the given enemies health along with its attack power (damage dealt).

### "Presentation"

Shown below is a short video presentation of the current progress.
The new UI can be seen (subject to change), containing a Health Bar as well as a field displaying the current score of the player character.

The first part of the animation shows the player picking up collectibles (with the diamond shaped gems each giving 100 points, and the square gem giving 250 points) and then completing the level by "reaching" the chest.

The second part shows the player taking damage by colliding with the enemy (without attacking) untill no health is left, and the player dies.

![Milestone 2 Video](/Labyrinth-Legends/resources/milestone2_death_and_level_complete.gif)