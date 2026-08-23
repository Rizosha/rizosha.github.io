---
title: Naked Man
published: 2021-09-01
updated: 2021-09-01
description: 'This project was a University Submission for Gameplay Programming.'
image: '/videos/NakedMan - Build(1).mp4'
tags: ["Featured"]
category: 'University'
draft: false 
---


<video src="/videos/NakedMan - Build(1).mp4" autoplay muted loop playsinline style="width: 100%;"></video>

# Overview

This project is a small rogue like prototype that I created for one my modules at university. Inspired by the game 
Enter the Gungeon, my aim was to create a 2D level in a 3D space with enemy AI roaming around the map for you to defeat.

# Character Controller

When creating the controller, I created a basic 2d character sprite in Aseprite with 6 different direction angles for the character to look towards based on the position of your cursor on the screen.

<img src="/Images/NakedMan/nakedmanEdit-Sheet-Recovered.png" alt="Character sprite sheet" style="width: 100%; object-fit: contain; border-radius: 12px;" />


As I wanted to mimic the game Enter the Gungeon, I was particular with the angles/directions the character could look
towards. I separated the screen into different sectors which matched ETG that provided the 6 directions and created a
script which would determine where the character was looking.

<img src="/Images/NakedMan/degrees.png" alt="Direction angle diagram" style="width: 99%; object-fit: contain; border-radius: 12px;" />


The script comprised of finding out where is true north (vector forward) and keeping track of the cursors vector location
by using a cube fixed to its own layer and storing its location. From this I can figure out what angle the cursor it at 
in comparison with the character. I then created checks at each desired angle point to update the characters animator
controller to change the characters sprite. On the image below the purple debug line is true north and the green debug 
line is the mouse direction

<div style="display: flex; gap: 10px; align-items: center; justify-content: center;">
  <video src="/videos/NakedMan/360.mp4" autoplay muted loop playsinline style="width: 32%; border-radius: 12px;"></video>
  <img src="/Images/NakedMan/sidedude.png" alt="Character rotation debug view" style="width: 32%; object-fit: contain; border-radius: 12px;" />
  <img src="/Images/NakedMan/angleanim.png" alt="Animator state machine for directions" style="width: 32%; object-fit: contain; border-radius: 12px;" />
</div>

```csharp
          //sets true north
          Vector3 north = Quaternion.Euler(-45f, 0, 0) * player.forward;
          //direction of mouse
          Vector3 direction = mouse.position - transform.position;
          //creates a reference from true north
          Vector3 cross = Vector3.Cross(north, direction);

          //calculates angle of north and mouse direction
          angle = Vector3.Angle(direction, north);

          if (cross.y < 0)
          {
              //makes the angle 360
              angle = (180 - angle) + 180;
          }

          //Big IF statement which sets the angles for the animator.
          if (angle >= 0 && angle <= 30)
          {
              aDirection = 1;
          }
          if (angle >= 30 && angle <= 60 )
          {
              aDirection = 2;
          }
          if (angle >= 60 && angle <= 150)
          {
              aDirection = 3;
          }
          if (angle >= 150 && angle <= 180)
          {
              aDirection = 4;
          }
          if (angle >= 180 && angle <= 210)
          {
              aDirection = 4;
          }
          if (angle >= 210 && angle <= 300)
          {
              aDirection = 5;
          }
          if (angle >= 300 && angle <= 330)
          {
              aDirection = 6;
          }

          if (angle >= 330)
          {
              aDire
          }

          // sets tof rotation
          animator.tion);
      }
```

I then set the character sprite and the player camera to be at a 45 degree angle along with setting the camera type to 
Orthographic to create the illusion of the game being 2D.

<img src="/Images/NakedMan/sideman.png" alt="Character mesh with collider gizmos" style="width: 50%; object-fit: contain; border-radius: 12px;" />


# Weapon

The player also has a weapon that can be aimed with the mouse. This works by taking the location of the mouse position 
to world space and saving it, creating a direction to the aim location. If the player clicks the fire button, a 
projectile will fire toward the direction saved. When the ammo runs out, the weapon will automatically reload and
prevent the player from firing for 1.4 seconds.

<div style="display: flex; gap: 10px; align-items: center; justify-content: center;">
  <video src="/videos/NakedMan/aim.mp4" autoplay muted loop playsinline style="width: 50%; border-radius: 12px;"></video>
  <img src="/Images/NakedMan/ammo.png" alt="Ammo UI bar" style="width: 50%; object-fit: contain; border-radius: 12px;" />
</div>

# Map Features

Using Aseprite and some online images, I was able to create some textures for the level. These were made so they are 
repeatable and can be used for the walls and floor.

<div style="display: flex; gap: 10px; align-items: center; justify-content: center;">
  <img src="/Images/NakedMan/Floortile-Recovered.png" alt="Floor tile texture" style="width: 50%; object-fit: contain; border-radius: 12px;" />
  <img src="/Images/NakedMan/Screenshot 2022-01-08 232735.png" alt="Wall tile texture" style="width: 50%; object-fit: contain; border-radius: 12px;" />
</div>

<div style="display: flex; gap: 10px; align-items: center; justify-content: center;">
  <video src="/videos/NakedMan/health.mp4" autoplay muted loop playsinline style="width: 50%; border-radius: 12px;"></video>
  <video src="/videos/NakedMan/health2d.mp4" autoplay muted loop playsinline style="width: 50%; border-radius: 12px;"></video>
</div>

I also created some pitfalls that the player can fall through by creating gaps in the floor. The way this works is that
the players last position is stored in a variable and is updated once per second if the character is grounded. If the 
character isn't grounded at the specified time, the player will return to the last position saved.

<video src="/videos/NakedMan/pitfall.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 12px;"></video>

Placed around the map are some health packs that the player can collect. I created a 3d box that resembles a med kit and
attached a script. The script checks to see if the player has entered the required radius around the pickup and checks 
to see if the player has pressed the required key to pick it up. The amount of health that is given is also capped so it
doesn't give the player more health than the maximum. I also added some coloured spotlights to highlight med packs and a
script to make it rotate around at a given speed.

<video src="/videos/NakedMan/health.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 12px;"></video>

<video src="/videos/NakedMan/health2d.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 12px;"></video>


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
