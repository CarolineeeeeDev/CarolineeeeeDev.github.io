---
layout:       post
title:        "Final Project Proposal"
author:       "Caroline飘小蝎"
header-style: text
catalog:      true
tags:
    - EAE
    - Assignment
    - C++
    - Game Engine
    - English
---

### Proposal: Two-Player Racing Game

#### Game Overview

I am developing a two-player racing game where each player competes to be the first to cross the finish line. The game will feature a 3D environment but will be viewed from a fixed, top-down perspective, making it appear as a 2D racing experience. Each player controls a vehicle and must dodge oncoming cars to avoid collisions, which will slow them down. The game will end when one player reaches the finish line, at which point they will be declared the winner.

#### Game Features

1. **Control Systems**:
   - Player 1 will use the keyboard to control their vehicle.
   - Player 2 will use a game controller (such as an Xbox controller) to control their vehicle.
2. **Game Mechanics**:
   - Vehicles will navigate a straight track filled with obstacles, represented by oncoming cars.
   - If a player collides with an oncoming car, their speed will decrease, giving the other player an advantage.
   - The game will include a simple physics system to handle vehicle speed changes upon collisions.
3. **End Conditions**:
   - The game will declare the first player to reach the finish line as the winner.
   - A log will print the results, indicating who won the race.

#### Engine System Utilization

I will be using my **Input System** to manage the controls for both the keyboard and the game controller. This system will handle input detection and mapping for the two different control schemes, ensuring that both players can interact with the game smoothly.

#### Other Engine System

I may integrate **Liu Yan’s Collision System** into the game. This system will detect when the player vehicles collide with obstacles (oncoming cars). The collision detection will trigger a response to slow down the colliding player's vehicle, creating a penalty for poor navigation.

#### Credit

- Collision System by **Liu Yan** will be used to manage all in-game collisions.