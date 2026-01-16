---
title: DnDice
published: 2024-01-01
updated: 2026-01-01
description: 'This is a project I created in University so that you can roll dice on your phone at DnD Campaigns with physics'
image: ''
tags: [DnDice]
category: 'University'
draft: false 
---

## Introduction
This project was a submission for my Advanced Games Programming module whilst at University. The premise for this 
project was to create a dice rolling game that can be used while playing Dungeons and Dragons. I wanted to create something 
that I would get use out of weekly during my sessions and could develop more after the submission date.


## Objectives

One of the main things I wanted to achieve was to create a launcher that grabs all the dice together in one spot and throws them in a direction.
I want some sort of explosive and chaotic launcher that will add a little extra emphasis to my rolls while playing that isn’t like the previous examples.
Along with this I wanted some sort of system to save the dice loadouts and assign a name to them
With this the player would be able to assign them the name of a spell or attack and pull out the dice straight away without the need to curate them again. 

I also need some modifier tab to modify the output of the dice The user would be able to have the option to either add a modifier to
each of the dice rolls or at the end of all the rolls without the need to calculate it at the table.
Based on the other dice rolling examples, they had some sort of spawning system for the dice which was based on a button press
My aim is to include a system which spawns the dice on the board on a button press.
Finally,I would need some sort of tally system of all the dice which considered the modifiers This would also include a display which is
half of all the current dice on the board


## Research

Google Browser Dice Game

This is the most basic iteration of a dice roller. With this you can select which dice you wish to roll, spawn them in and roll them. 
In the corner is a total of all the dice, along with an extra button that allows you to make modifications to your rolls (add an extra value to it)

Dice - Play store 

This is a game on the Play Store called Dice.

This is the first example of a game that's already been made in Unity and will work similarly to how I want. The main mechanic from this game is when you have
selected your dice, you will tap the screen to add a bounce to all the dice, which will also apply a rotating force in order to roll them.
Along with this there are board customizations, more variety of dice such as a D1000 and other options to increase the gravity and such.

Indie Dev Online - Dice with physics 

One of my friends heard about what I was doing and suggested this dice game that a Reddit user posted.
He wanted to roll the dice similarly to how I did and have them react to physics instead of relying on a number generator.
When you click on the screen all the dice will bounce at once and roll around.



## Dice Output

Originally, my first plans to calculate the total of the dice consisted of using ground checks on each of the dice.

From this, I knew I would need to store all the dice in some array and use a loop to perform a ground check as soon as the velocity reached 0.

Planning this out early though highlighted one key issue, if I had a die such as a D20, that would mean there would be 20 ground checks being calculated at the same time.
Using 5 D20 alone would be equal to 100 ground checks in one instance. This would be a huge performance hit, and would need to find an alternative solution.

During class, the tutor asked if any of us had any issues with our projects at the moment, and I asked if there was a better way to calculate this.

After some discussion, we settled that it would be more efficient to create reference points for each side of a die and store it inside an array.
From here, we select the reference point that has the highest Y value, and that will be the side that which was rolled. 

To execute this, I started by creating a script that would store the reference points for each of the sides of the dice. After storing them, 
I created a separate array that took the data from the first array and stored the Y values of each reference point. From here I was able to sort through the array and find the highest Y value outputting the value of the dice.

## Shooting mechanic 

I then tried to plan out my shooting mechanic. Using the diagram below, I mapped out that when a finger input is recieved, it would gather all the dice and
move them to the point of your finger. When you slide your finger away from the original point, it will create a slingshot between the two points. 
When you release your finger, it will then release all the dice and fire them in the direction that was created between the two points. 

When creating this in Unity, I created a script that would house reference points for the dice along with its Rigid Body and created reference points for the touch input.
I was then able to create a function that would move the dice to the point of the finger input and then create a slingshot between the two points. I also had 
to create an offset for the dice to sit below the camera, as originally they would be taking the whole screen when gathered under your finger. 

I also needed a way to "shuffle" the dice before they are fired. I was able to do this by using the Ping Pong function to mimic a left,right,up,down 
force by pinging between two values which represented the dice current rotation. Although I realised this wasn't the most efficient way to do this, I was able to 
create a function that would shuffle the dice by using a random number generator to determine the direction and force of the dice. A much simpler method would have just been to set the 
rotation of the dice based on a random number. However, I figured this would be more interesting of a mechanic and would let me get use out of the PIng POng Function as I had never had a use for it before. 

## User Interface 

## Dice Spawning 

## Custom Dice Save System 






