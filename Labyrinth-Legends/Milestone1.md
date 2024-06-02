# Milestone 1 - POC and basic functionality

This developer update will describe the first milestone in the development of Labyrinth Legends.

## Goals
The main goal of this first milestone is to have a functional level to serve as a "***Proof of Concept***" of the game and its functionality.

The main goals for this milestone is:
- To have a controllable player character.
- A simple level that the player character is able to navigate through.
- Collectibles to pick up while navigating the level, as well as a point/scoring system.

## Delimitations:
This "***Proof of Concept***" should be seen as an "*alpha*"-release of sorts, meaning that the functionality has been the main focus of this phase of development. Therefore, all assets (tilesets, sprites and UI elements) are not final.

## Work done

### Project Setup and main sources of reference

The game project has been setup using the 2D URP (*Universal Render Pipeline*) template, and the basic setup of the first (and currently the only) scene is made with knowledge gathered from the following 2 official Unity tutorials:

- [Roll-a-Ball](https://learn.unity.com/project/roll-a-ball?uv=2022.3)
- [Rubys Adventure](https://learn.unity.com/project/ruby-s-2d-rpg?uv=2020.3)

Using the second of the two involved quite a bit of trial and error to get working properly, as the tutorial is made with the "standard" 2D template, and is also written for an older version of the Unity engine (2020.3).

![Milestone 1 Video](/Labyrinth-Legends/resources/LL_Milestone1.gif)


### Level
As the game is a top-down 2D game, the playable area of the level is implemented by creating two tilemaps (Floors and Walls), with the latter having a Tilemap Collider component attached to it, in order to make sure that the player cannot navigate outside of the corridors of the level.

### Player Character
The player character is a central element of the game, so implementing a "*proof of concept*" for it was deemed essential as part of the first milestone. Adhering with the *Single Responsibility*-principle of SOLID, the code-implementation of the player is handled by different scripts, each dealing with one single responsibility:

- PlayerInputController, responsible for receiving input.
- PlayerMovemenetController, responsible for converting the received input to player movement.
- PlayerCollisionController, responsible for handling collision events.

Each of these (and more to come) will probably be expanded upon as development continues.

### Camera
The only change made to the default Main Camera-element, is the addition of the *CameraController*-script, making the camera follow the player as it moves around the level.

### Collectibles and points
Another key focus of the game is the point-system. This is, for now, implemented by having collectibles in the level which, when collided with, adds a set number of points to the player. For now, only one kind of collectible is created, but in the future different collectibles (each with a different point-value) is going to be added.
