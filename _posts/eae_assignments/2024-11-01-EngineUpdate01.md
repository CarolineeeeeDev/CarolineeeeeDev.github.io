---
layout:       post
title:        "Game Engine Update 01"
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

## Overview

This week, I focused on adding a player input subsystem to the original engine, specifically implementing the following features:

- Replace the old user input system with the new player input system
- Key binding functionality
- Update player input
- Update game object position
- Update camera position
- Switch game object meshes
- Input for exiting game

## New player input system

<img src="\assets\eae\assignment9\1.png" style="zoom:50%;" />

The latest player input system can effectively replace the original user input system in `cMyGame`.

Additionally, it utilizes some methods from the previous user input system, such as `IsKeyPressed`, to detect when a player presses a specific key.

## Key Binding

<img src="\assets\eae\assignment9\2.png" style="zoom:50%;" />

The implementation of key binding in the player input system allows for a flexible and customizable way to map specific actions to user-defined keys. By using an enumeration for action types, such as moving forward, backward, switching meshes, and quitting the game, developers can easily associate each action with a specific key code. This design enables players to customize their controls according to their preferences, enhancing their overall gaming experience.

**Benefits of this design include:**

1. **User Customization:** Players can remap keys to suit their personal play style, leading to a more comfortable and engaging gaming experience.
2. **Scalability:** New actions can be added easily without modifying the existing codebase. Developers can simply define new action types and bind them to the desired keys.
3. **Maintainability:** The clear separation of key bindings from game logic improves code readability and maintainability. Changes to key mappings do not affect the underlying game mechanics.
4. **Consistency:** Using a centralized input management system ensures consistent handling of input across different game states and contexts, reducing the likelihood of errors.

## Update player input

<img src="\assets\eae\assignment9\3.png" style="zoom:50%;" />

The `Update` method in the `PlayerInput` system is designed to capture and process user input each frame, updating the state of player actions based on the current key presses. This method retrieves the current state of input, including movement direction and action triggers, and fills an `InputState` structure with the corresponding values. It does this by checking which keys are pressed and translating those inputs into meaningful actions that the game can recognize

## Update game object position

<img src="\assets\eae\assignment9\4.png" style="zoom:50%;" />

The game object position update mechanism is crucial for ensuring that the objects in the game world respond correctly to player inputs. The `Update` method processes the movement direction derived from the player's input and applies it to the velocity of the game objects. This enables smooth movement in response to key presses, allowing for a fluid gameplay experience.

By resetting the object's velocity each frame and then applying the player's desired direction, the system ensures that movement is both responsive and intuitive. This design allows for natural interactions, such as accelerating and decelerating based on player input, thereby enhancing the overall gameplay dynamics.

## Update camera position

<img src="\assets\eae\assignment9\5.png" style="zoom:50%;" />

The camera position update is vital for maintaining an optimal view of the game environment as players interact with it. In the updated player input system, camera movement is tied directly to player inputs, allowing the camera to follow the player's actions seamlessly.

By resetting the camera's velocity each frame and applying movement based on input, the system ensures that the camera remains fluidly aligned with the player's perspective, which is essential for immersion. This feature also includes smooth transitions to provide players with a consistent visual experience while navigating the game world.

## Switch game object meshes

<img src="\assets\eae\assignment9\6.png" style="zoom:50%;" />

The ability to switch game object meshes dynamically enhances gameplay variety and visual appeal. This feature allows developers to change the appearance of objects based on player actions or game events, creating a more engaging and visually diverse experience.

The implementation involves binding specific input actions to mesh switching functionalities, allowing players to change how objects look during gameplay. For example, switching between different character skins or weapon types can make gameplay feel fresh and exciting.

## Input for exiting game

<img src="\assets\eae\assignment9\7.png" style="zoom:50%;" />

<img src="\assets\eae\assignment9\8.png" style="zoom:50%;" />

The exit game input functionality provides players with a straightforward method to exit the game when desired. By binding the escape key to an exit function, players can quickly terminate the game, ensuring an intuitive user experience.

This implementation is crucial for maintaining good user experience, as it respects player autonomy and provides a clear way to exit the game. It also includes necessary cleanup operations to ensure that all resources are properly released when the game is closed.
