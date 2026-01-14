---
title: DnDice
slug: dndice
published: 2024-01-01
updated: 2026-01-01
description: 'This is a project I created in University so that you can roll dice on your phone at DnD Campaigns with physics'
image: 
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
I want some sort of explosive and chaotic launcher that will add a little extra emphasis to my rolls while playing that isn’t like the following examples below.
Along with this I wanted some sort of system to save the dice loadouts and assign a name to them.
With this the player would be able to assign them the name of a spell or attack and pull out the dice straight away without the need to curate them again. 

I also need some modifier tab to modify the output of the dice The user would be able to have the option to either add a modifier to
each of the dice rolls or at the end of all the rolls without the need to calculate it at the table.
Based on the other dice rolling examples, they had some sort of spawning system for the dice which was based on a button press
My aim is to include a system which spawns the dice on the board on a button press.
Finally,I would need some sort of tally system of all the dice which considered the modifiers This would also include a display which is
half of all the current dice on the board

### Research

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

### Planning

Originally, my first plans to calculate the total of the dice consisted of using ground checks on each of the dice. 

From this, I knew I would need to store all the dice in some array and use a loop to perform a ground check as soon as the velocity reached 0. 

Planning this out early though highlighted one key issue, if I had a dice such as a D20, that would mean there would be 20 ground checks being calculated at the same time. 
Using 5 D20 alone would equal to 100 ground checks in one instance. This would be a huge performance hit, and would need to find an alternative solution.

During class, the tutor asked if any of us had any issues with our projects at the moment, and I asked if there was a better way to calculate this. 


