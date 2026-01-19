---
title: DnDice
published: 2024-01-01
updated: 2022-01-01
description: 'This is a project I created in University so that you can roll dice on your phone at DnD Campaigns with physics'
image: ''
tags: [DnDice]
category: 'University'
draft: false 
---

# Introduction

This project was created as a submission for my Advanced Games Programming module at university. The goal was to develop a dice-rolling game that could be used while playing Dungeons and Dragons.

Rather than building something purely for assessment, I wanted to create a tool I would genuinely use during my weekly DnD sessions. I also aimed to design it in a way that allowed me to continue developing and expanding it after the module submission date.

# Objectives

One of my main goals was to create a launcher system that gathers all selected dice into one place and fires them in a chosen direction. I wanted this launcher to feel explosive and chaotic, adding extra impact to dice rolls instead of behaving like more traditional dice rollers.

Another key objective was a dice loadout system. Players should be able to save specific dice combinations, assign them a custom name, and instantly reuse them. This allows dice sets to be named after spells or attacks, removing the need to repeatedly curate the same dice.

I also wanted a modifier system that could adjust dice results automatically. The user should be able to apply modifiers either per die or as a final total without needing to calculate anything at the table.

Most existing dice rollers rely on simple button-press spawning. Instead, my aim was to create a system where dice spawn onto the board through a dedicated interaction and can then be physically launched.

Finally, I needed a tally system that calculates the total of all dice, including modifiers. This also includes a secondary display that shows half of the current total, which is useful for large damage rolls.

# Development

## Dice Output

My initial approach to calculating dice values involved using ground checks on each die. Once a die’s velocity reached zero, it would perform a ground check to determine which face was facing upward.

While planning this, I quickly identified a major problem. A D20 would require 20 ground checks at once, meaning just five D20s would trigger 100 checks simultaneously. This would cause unnecessary performance issues, so I needed a better solution.

After discussing this with my tutor during class, we agreed that using reference points would be far more efficient. Each side of a die has a reference point, all of which are stored in an array. By checking which reference point has the highest Y value, I can determine which face is facing upward.

To implement this, I created a script that stores the reference points for each side of the die. These points are added to an array, and their Y values are extracted into a second array. By sorting and comparing these values, I can identify the highest point and return the correct dice result efficiently.

## Shooting Mechanic

For the shooting mechanic, I began by planning the interaction visually. When the player touches the screen, all active dice gather at the touch point. Dragging the finger away creates a slingshot between the start and end points. When released, all dice are fired in that direction.

In Unity, I implemented this by creating a script that stores references to each die, its Rigidbody, and the touch input positions. A function moves the dice to the touch point and calculates the launch direction based on the distance between the two points. I also added an offset so the dice sit slightly below the camera, as they initially took up too much screen space when grouped together.

Before firing the dice, I wanted a way to shuffle them so the rolls felt more natural. I first experimented with Unity’s PingPong function to simulate left, right, up, and down motion by oscillating between rotation values. Although this was not the most efficient solution, it worked well as a learning exercise.

Later, I refined the system to use random values for both direction and force. A simpler option would have been to randomise rotation directly, but the physical shuffling added extra energy to the mechanic and gave the rolls more personality.

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




