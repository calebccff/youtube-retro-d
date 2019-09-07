Hi, welcome back. After a much longer break than I would have liked I've finally had a chance to work on another video, I start University in a few weeks so it might be another long break before episode 3 - I figured it was worth putting something out now.
This episode we're going to be creating a player and some basic physics for our asteroids game.

# Last Episode
> Show clips of end of last episode 
If you haven't already seen the introduction video, you can see it in the cards or down in the description - check it out if you don't have Dlang and DSFML already installed on your system!
Now that we're all rearing to go it's time we actually wrote some real code!

# Design
When creating a game like this it's important to consider how we want our program to flow. We know we can run code at startup to do things like create the window, and we have a loop in which we can handle events and draw to our canvas. We'll keep it simple and start with the key part of our game, the player.
> Picture of player
The player needs to be able to move, shoot bullets and be drawn to the screen, these are all "thing" that will be done with the player, therefore it makes sense to group them all together. They all also need to know things like the location of the player, what direction the player is facing and what the player looks like, so we should group those together too.
If you don't see what I'm getting at yet, we'll be using an OO model.
> Start writing player class
There are a few ways in which you can design a "player" in this sense, in C you'd create a player struct and some functions that take the struct as a parameter and performs operations using the struct properties (Like moving the player). This approach still works fine however in order to make things a bit simpler, we'll use an abstraction to do this for us.
Like many modern languages, D supports object oriented programming, we can define classes that contain properties and methods, create instances of them called 'objects' and use that object to represent something like a player that has state - if you're unsure on what "state" is I've provided some useful resources down below, let me know if you'd like me to make a video about it.

Our player class will need to know a few things, these are called the properties as they represent the state of our player. The most obvious of these are the location and direction but there are a few more, it also makes sense to store the velocity of the player, we know this is state because it has a direct, perceivable effect on the player - they will start moving at a different speed.



As we're only building an arcade game, it makes sense to assume that we only have a few game states, the main menu, in game, and the game over screen.

> Diagram of game states?
As these can all be interacted with, they will have to be a part of our draw loop


# Description
Part 1: https://www.youtube.com/watch?v=3Yr2Nq78p_0
State:
    Check out this interesting stackoverflow post: https://softwareengineering.stackexchange.com/questions/150120/definition-of-state
    The state of a program represents the values of all the variables than can change - If you've ever used an emulater, that's where the term "save state" comes from.