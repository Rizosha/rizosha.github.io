---
title: CrumbleJack
published: 2025-08-31
updated: 2025-08-31
description: 'This Project was created for the Brackeys 2025.2 Game Jam with a theme of risk it for a biscuit.'
image: '6U6MYP.png'
tags: []
category: 'Game Jam'
draft: false 
---

<style>
.custom-md img[src*="6U6MYP.png"] {
    display: none;
}
</style>


<iframe frameborder="0" src="https://itch.io/embed-upload/14825707?color=b86f50" allowfullscreen="" width="900" height="585"><a href="https://rizosha.itch.io/crumblejack">Play CrumbleJack on itch.io</a></iframe>

# Overview

This project was made for the Brackeys Game Jam 2025.2 in just 1 week. The theme for the game jam was "Risk it for a Biscuit" and we collectively came up with a blackjack style game that was based on biscuits.


# My Contributions

Blackjack core gameplay loop
Dealer system
Dialogue system
Jammie Animations 







<!--

# Blackjack Mechanics

## Starting a Round

Each round begins when the player presses the Deal button. This triggers the main entry point of the game loop.

Before anything happens, the game checks whether it should even continue. If the player has already reached the win condition or run out of rounds, the game ends immediately. This prevents unnecessary processing and ensures the game flow stays clean.

If the game is still active, the system then checks whet/her the player has enough chips to place their current bet. If they do, the bet is deducted and the round officially begins. At the same time, the UI for changing bets is disabled so the player is locked into their decision.

From here, the game transitions into the setup phase.

## Resetting the Table

Before dealing new cards, the game clears everything from the previous round. Both the player and dealer hands are emptied, and any card objects in the scene are destroyed. This ensures there’s no leftover state that could interfere with the new round.

The deck is also reset and shuffled, guaranteeing that each round starts fresh.

Once everything is cleared, the game begins dealing cards.

## Dealing the Initial Hands

The game deals two cards to the player and two to the dealer, alternating between them to mimic real Blackjack dealing. This is done using a coroutine, which allows short delays between each card so the process feels animated rather than instant.

As each card is dealt, it is added to the appropriate hand and displayed visually on the table.

Once both hands are dealt, the game calculates the total value of each hand and sets the game state to active. This is the moment where the player gains control.

## Calculating Hand Values

Hand values are calculated by summing the value of each card. Face cards are worth 10, number cards are worth their number, and Aces are handled dynamically.

Aces are initially treated as 11, but if the total hand value exceeds 21, they are converted to 1 by subtracting 10 from the total. This continues until the hand is valid or there are no more Aces to adjust.

This system ensures that the classic Blackjack rule for Aces is correctly implemented.

## Blackjack Checks

Right after the initial deal, the game checks for instant outcomes.

If the player has exactly 21, they win immediately unless the dealer also has 21, in which case it’s a draw. This ends the round early and pays out accordingly.

Interestingly, the dealer is prevented from starting with a Blackjack. If their initial hand totals 21, the hand is discarded and redrawn. This is a design choice that slightly favors the player and keeps the game moving.

## Player Turn: Hit or Stand

Once the round is active, the player can choose between two actions: Hit or Stand.

## Hit

When the player hits, a new card is drawn and added to their hand. The total is recalculated immediately.

If the new total is exactly 21, the player wins instantly and the round ends.

If the total exceeds 21, the player busts and loses the round. The game then disables further input and prepares for the next round after a short delay.

If neither of these conditions is met, the player can continue hitting.

## Stand

When the player stands, they end their turn and pass control to the dealer. At this point, the player can no longer take actions, and the game transitions into the dealer’s turn.

Dealer Turn: Automated Play

The dealer follows a fixed set of rules, just like in traditional Blackjack.

First, the dealer’s hidden card is revealed. Then, the dealer begins drawing cards according to a simple rule: keep drawing while the hand value is 17 or less.

Each card draw is spaced out with a short delay to maintain a sense of pacing and animation.

Once the dealer’s total exceeds 17, they stop drawing and the game moves to the final comparison.

## Determining the Winner

At the end of the dealer’s turn, both hands are compared.

There are three possible outcomes:

If the dealer busts or the player has a higher total, the player wins.
If both totals are equal, the round is a draw and the player’s bet is returned.
If the dealer has a higher total, the dealer wins.

When the player wins, they receive double their bet. If it’s a draw, they simply get their original bet back. If they lose, the bet is gone.

## Ending the Round

After the result is determined, the game sets its active state to false. This effectively locks out any further player actions and signals that the round is over.

UI elements are re-enabled so the player can place a new bet, and after a short delay, the table is cleared automatically to prepare for the next round.

The Game Loop in One Sentence

The entire system can be summarized simply:

The player places a bet, cards are dealt, the player chooses to hit or stand, the dealer plays automatically, the winner is decided, and the game resets for the next round.

## Why This System Works

What makes this implementation solid is its clear structure and separation of phases. Each part of the game — dealing, player actions, dealer logic, and resolution — is handled in order, with a single boolean (gameActive) controlling whether the round is in progress.

Coroutines are used to control timing and pacing, making the game feel smooth and responsive rather than instantaneous.

Overall, it’s a straightforward but effective Blackjack loop that mirrors the real game while fitting neatly into Unity’s update and event system.

# Deck

# Card dealing animation 

# Betting system 

# Jammie Animation & Dialogue

# Win Animation

-->
