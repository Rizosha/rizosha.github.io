---
title: Too Much To Chew
published: 2021-04-20
updated: 2021-04-20
description: 'This Sidescrolling Endless Shooter was my first group project while at University.'
image: './TMTCTitlescreen.png'
tags: [TooMuchToChew]
category: 'University'
draft: false 
---


<iframe frameborder="0" src="https://itch.io/embed-upload/17394865?color=080547" allowfullscreen="" width="960" height="660"><a href="https://rizosha.itch.io/too-much-to-chew">Play Too Much To Chew on itch.io</a></iframe>

<br/>

<iframe frameborder="0" src="https://itch.io/embed/3556418" width="552" height="167"><a href="https://rizosha.itch.io/too-much-to-chew">Too Much To Chew by Rizosha</a></iframe>

<br/>

---

# Overview

This game was my first group collaboration project that I worked on while at university. The premise for the game was an
endless scrolling shooter, where a scientist was trying to end world hunger by creating superfoods. His experimentation 
went wrong, and now his superfoods threaten the world. As this was one of my first projects, it serves as a reminder to
how far I have come in my development journey.

<br/>

# Contribution List

- Movement  
- Shooting mechanic  
- Enemy Spawner  
- Health Spawner  
- Background Image scrolling  
- Score System 
- Scientist Sprite  
- Rocks Sprite  
- Enemy Animations  

<br/>

<!-- 

# Development

## Movement

When the player presses W or S, the target position of the scientist shifts up or down by a fixed amount using a variable 
“stepSize”, as long as it stays within the defined maxHeight and minHeight bounds. Rather than snapping the object
instantly to that position, FixedUpdate smoothly interpolates the rigidbody toward the target each physics frame using
Vector2.Lerp, with moveSpeed controlling how fast it travels to the next lane.

## Shooting Mechanic

To create the shooting mechanic, I created a script which that attaches to the pellet game object moving the rigidbody 
component to the right at a given speed. This is then instantiated into the scene whenever the player presses the
spacebar. I also added a box collider to destroy the bullet on collision.

## Spawners

I created some prefabs of the enemies where they used a similar system to the bullet to travel to the left of the screen
into a box collider to destroy them. I then saved the enemies as prefabs and created 3 empty game objects where I wanted
to spawn them from. I then stored the transforms of the game objects in an array and created an index which generated a 
random number from 0 to the length of the Spawn Points array to alternate where the enemies spawned from. 

```csharp title="Spawn Example 1"
spawnIndex = Random.Range(0, spawnPoints.Length);
Instantiate(donut, spawnPoints[spawnIndex].position, Quaternion.identity);
```
I then used the InvokeRepeating command to spawn in these enemies at alternating times by using Random.Range.

```csharp title="Spawn Example 2"
InvokeRepeating("SpawnDonut", 0, Random.Range(2f,6f ));
```

I then created levels to the game by creating a switch with case statements. This switch would start at phase one when
the game starts and change when the player receives a certain amount of points, advancing them through the levels and
adding in more enemies and obstacles.

```csharp title="Spawn Example 3"
private void Update()
{
 if (score == null) return;
 
 switch (currentPhase)
 {
 case Phase.PhaseOne:
 if (score.pScore >= phaseTwoThreshold)
 TransitionTo(Phase.PhaseTwo);
 break;

 case Phase.PhaseTwo:
 if (score.pScore >= phaseThreeThreshold)
 TransitionTo(Phase.PhaseThree);
 break;
 }
}
```

```csharp title="Spawn Example 4"
void TransitionTo(Phase newPhase)
{
 currentPhase = newPhase;
 CancelInvoke("SpawnBurger");
 CancelInvoke("SpawnBoulder");
 CancelInvoke("SpawnDonut");
 CancelInvoke("SpawnWall");

 switch (currentPhase)
 {
 case Phase.PhaseOne:
 InvokeRepeating("SpawnDonut", 0, Random.Range(2f,6f ));
 InvokeRepeating("SpawnBoulder", 4f, Random.Range(4f, 9f));
 break;

 case Phase.PhaseTwo:
 InvokeRepeating("SpawnDonut", 1f, Random.Range(1f,5f ));
 InvokeRepeating("SpawnBurger", 0f, Random.Range(1f, 7f));
 InvokeRepeating("SpawnBoulder", Random.Range(4f,9f), Random.Range(4f, 9f));
 break;

 case Phase.PhaseThree:
 InvokeRepeating("SpawnDonut", 2, Random.Range(1f,4f ));
 InvokeRepeating("SpawnBurger", 2f, Random.Range(1f, 5f));
 InvokeRepeating("SpawnBoulder", Random.Range(4f,9f), Random.Range(4f, 9f));
 InvokeRepeating("SpawnWall", 0f, Random.Range(4f, 9f));
 break;
 }
``` 


## Image Scrolling

For the background, I created a material for both the road and the city and added in the PNG images that were created by
my team. I was then able to take the material and apply an offset as a moving Vector2, producing the scrolling effect. 

-->
