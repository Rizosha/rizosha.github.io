---
title: DnDice
published: 2024-01-01
updated: 2022-01-01
description: 'This is a project I created in University so that you can roll dice on your phone at DnD Campaigns with physics'
image: ''
tags: ["Featured"]
category: 'University'
draft: false 
---

<iframe
  width="720"
  height="405"
  src="https://www.youtube.com/embed/I5Bx0ryJFtM?autoplay=1"
  title="YouTube video player"
  frameborder="0"
  allow="autoplay; encrypted-media"
  allowfullscreen>
</iframe>


---

<br />

<br />

# Introduction

This project was created as a submission for my Advanced Games Programming module at university. The goal was to develop a dice-rolling game that could be used while playing Dungeons and Dragons.

Rather than building something purely for assessment, I wanted to create a tool I would genuinely use during my weekly DnD sessions. I also aimed to design it in a way that allowed me to continue developing and expanding it after the module submission date.

<br />

# Development

## Dice Output

My initial approach used ground checks on each die face to determine which side was facing up once the die stopped rolling — but a D20 would require 20 simultaneous checks, meaning five D20s alone would trigger 100 at once.

After revisiting this I landed on a more efficient solution using reference points. Each face has a reference point stored in an array, and by finding which has the highest Y value, I can determine the upward face. A script extracts these Y values into a second array, sorts them, and returns the correct result.


## Shooting Mechanic

For the shooting mechanic, the player touches the screen to gather all active dice at that point, then drags to create a slingshot effect — releasing fires the dice in that direction.

In Unity, a script stores references to each die, its Rigidbody, and the touch positions. It moves the dice to the touch point, calculates the launch direction from the distance between both points, and applies a slight camera offset so the grouped dice don't fill the screen.

Before firing, I added a shuffle mechanic to make rolls feel more natural. I initially used Unity's PingPong function to oscillate rotation values, then refined it to use random direction and force values instead — the physical shuffling added extra energy and gave the rolls more personality.

## User Interface

I created a results display that activates once all dice velocities reach zero. This shows the total value of the roll and includes a secondary calculator that automatically displays half of the total for convenience.

A modifier button was added to the dice case, allowing players to apply bonuses or penalties either to each die or as a final value. This makes it quick and easy to account for buffs, debuffs, or situational modifiers during gameplay.

## Dice Spawning

To build the dice case, I used simple cube meshes with a wooden texture sourced online. Inside the case, dice are spawned using a global UI canvas that contains buttons for each dice type.

Dice spawning is handled using object pooling to improve performance and support large numbers of dice. Whenever a die is spawned, it is added to a list that is later used by the launcher system.

I also added simple animations for opening and closing the dice case. This includes moving the case partially into view and then sliding it off-screen at a slight angle to keep the interface visually dynamic.

## Custom Dice Save System

I implemented a system that allows players to save custom dice sets for later use. This removes the need to repeatedly spawn the same combinations of dice.

The system works by writing the dice array data to a JSON file along with a custom name. When saving a set, a new UI button is created using this name. Pressing the button instantly reloads the saved dice configuration.

I designed the interface to support up to 20 saved dice sets, using scroll views to keep the layout clean and manageable.

# Conclusion

Overall, I am very happy with the outcome of this project. It was one of my first projects completed entirely without following video tutorials, relying instead on my own knowledge and problem-solving.

The project significantly improved my understanding of arrays, data storage, and file writing. Planning mechanics using pseudocode also proved invaluable, especially for more complex systems like the shooting mechanic, as it allowed me to clearly define each step before implementation.

I would love to continue developing this project in the future. After researching existing dice simulators, I found that there are surprisingly few high-quality options available. Future improvements could include a visible launcher indicator to clearly show firing direction, as well as achievements, cosmetics, and further visual polish.




