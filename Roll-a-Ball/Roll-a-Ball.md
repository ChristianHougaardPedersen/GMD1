# Roll-a-Ball #

This game was made by following the official Unity tutorial (found here: [Roll-a-Ball Tutorial](https://learn.unity.com/project/roll-a-ball?uv=2022.3))

### Playable browser-version of the game can be found here: [Roll-a-Ball](https://christianhougaardpedersen.github.io/roll_a_ball_deployment/). ###

In this game, you navigate a ball around an obstacle course, using the arrow keys, while collecting pick-ups. Once all 12 pick-ups are collected, the game is won.

## Process ##

Going through the tutorial was a great way of learning the basics of the Unity Editor as well as the scripting. The tutorial is easy to follow, and is composed of multiple steps - each accompanied by a video for the more visually inclined. As i found the videos a bit tedious and "slow" to get through, i opted to just use the written steps instead, and followed the tutorial to the end before starting to expand the game a bit.

### Extended Version ###
After going through the tutorial, I had a very basic version of the game, which allowed the player to roll the ball around a square course while collecting 12 pickups lined in a rough circle around the starting position.
We were tasked with expand the game with additional elements, so i decided to extend the course to an L-shape by adding a new "Ground" (Plane) element, as well as adding obstacles to the level in order to make the game a bit more challenging. The obstacles are all placed in a new hierarchy, and were made simply by adding new 3D objects to the scene.
Other than this extension of the level itself, i decided to add a timer to the level, in order to introduce a new challenge to the game: How fast can you complete the level?

The timer is implemented by adding a new **TextMeshPro** element, and placing it in the upper right corner of the screen -  following the same logic as shown for the "pickup-counter" in the tutorial.
The **PlayerController**-script was then altered, by introducing the new **TextMeshPro**-object, a variable for storing the elapsed time (since the game was started) as well as a boolean variable to keep track of whether the level is completed (and therefore whether the timer should be stopped).
The timer is implemented by initializing the **elapsedTime**-variable to 0 when the **Start()**-method is called (upon game initialization), and then updating it in the **FixedUpdate**-method to add time elapsed between the last and current frame to the counter. After updating the variable, the text in the **TextMeshPro**-element is updated in order to show the time.
Finally, when the game is initialized, the **gameInProgress**-variable is set to true - and set to false when the last pickup is collected.

![Screenshot of the changes made to the PlayerController file.](/Roll-a-Ball/images/PlayerController.png)
![Screenshot of the game as it is currently.](/Roll-a-Ball/images/Gameplay.png)



I plan to update the game further in the future, as time and my knowledge reagarding Unity improves - and here is a rough outline of ideas for extension/improvement i have for the game:
- Implement a jump-mechanism to the game (I tried doing this, but got stuck on a problem where i could not figure out how to disallow "multiple jumps" at once - leading to the player being able to jump indefinately high).
- Implement additional levels.
- Implement a "restart" function, which allows the player to reset the current level at will (instead of having to reload the page, as it is currently).
- Implement a "high-score"-system for each level, in order to let the player compete (either against themself or others online) about completing the level in the shortest amount of time - hereby drastically increasing "replayability". This would, however, probably entail having some sort of (albeit very simple) database hooked up to the game - but this will be looked into in the future.
