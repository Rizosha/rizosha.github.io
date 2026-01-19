---
title: Naked Man
published: 2021-09-01
updated: 2021-09-01
description: 'This Project was created for the Brackeys 2025.2 Game Jam with a theme of risk it for a biscuit.'
image: ''
tags: [DnDice]
category: 'University'
draft: false 
---
# Overview

This project is a small rogue like prototype that I created for one my modules at university. Inspired by the game 
Enter the Gungeon, my aim was to create a 2D level in a 3D space with enemy AI roaming around the map for you to defeat.

# Character Controller

As I wanted to mimic the game Enter the Gungeon, I was particular with the angles/directions the character could look
towards. I separated the screen into different sectors which matched ETG that provided the 6 directions and created a
script which would determine where the character was looking.

The script comprised of finding out where is true north (vector forward) and keeping track of the cursors vector location
by using a cube fixed to its own layer and storing its location. From this I can figure out what angle the cursor it at 
in comparison with the character. I then created checks at each desired angle point to update the characters animator
controller to change the characters sprite. On the image below the purple debug line is true north and the green debug 
line is the mouse direction

I then set the character sprite and the player camera to be at a 45 degree angle along with setting the camera type to 
Orthographic to create the illusion of the game being 2D.

# Weapon

The player also has a weapon that can be aimed with the mouse. This works by taking the location of the mouse position 
to world space and saving it, creating a direction to the aim location. If the player clicks the fire button, a 
projectile will fire toward the direction saved. When the ammo runs out, the weapon will automatically reload and
prevent the player from firing for 1.4 seconds.

# Map Features

Using Aseprite and some online images, I was able to create some textures for the level. These were made so they are 
repeatable and can be used for the walls and floor.

I also created some pitfalls that the player can fall through by creating gaps in the floor. The way this works is that
the players last position is stored in a variable and is updated once per second if the character is grounded. If the 
character isn't grounded at the specified time, the player will return to the last position saved.

Placed around the map are some health packs that the player can collect. I created a 3d box that resembles a med kit and
attached a script. The script checks to see if the player has entered the required radius around the pickup and checks 
to see if the player has pressed the required key to pick it up. The amount of health that is given is also capped so it
doesn't give the player more health than the maximum. I also added some coloured spotlights to highlight med packs and a
script to make it rotate around at a given speed.

# Enemy AI

For the enemy AI, I created a script that would contain the logic and behaviour for patrolling across the map and 
targeting the player. To achieve this, I created a state machine that would have 3 states, Patrol, Chase and Attack.

# Patrol State

In the Patrol state, I created co ordinates that the enemy can randomly choose between, allowing them to move around 
using a NavMesh. When the enemy has reached its target destination, it will create the shortest path from its current 
position to the new selected destination and travel along it while looking out for the player.

# Chase State

For the Chase state, if the player moves into a specified radius near the enemy, the direction of the enemies movement 
will change to the players last known location and track him down and follow him at a set distance. If the Player leaves
this radius, the enemy will stop chasing the Player and return back to patrolling the level.

# Attack State

In the attack state, the enemy will now try to aim and shoot at the player. If the player is hit by any of the enemy
projectiles, the player will take set damage.

# Berserk State

In the case of the cube enemy, I added an extra berserk state to add some variety to the enemies by increasing their
rate of fire and attack range. This will trigger once the enemy is taken to less than half health.

# Win Condition

Once all of the enemies have been defeated, this will trigger the win condition by spawning a key pickup at the end of 
the level. Once the player picks this up by walking over and pressing the interact button, the player can now open the 
sealed door and complete the stage.

# Outcome

Through this project, I gained valuable knowledge in creating a functional 2.5D game. Until this point I hadn’t had much
experience with creating character controllers, and even though the sprite creation was time consuming and unfinished, 
I am still pleased with what I accomplished.

This was also one of my first experiences with creating a basic AI and becoming familiar with state machines. Also 
learning about object pooling for spawning in objects such as bullets to save on performance has proven to be invaluable.

There are still a few improvements that I would like to make to this game such as adding in an extra final boss and
improving the current shooting mechanic, as they would make this project feel a little more polished.