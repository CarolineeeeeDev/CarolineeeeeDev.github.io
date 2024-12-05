---
layout:       post
title:        "Final Project"
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

## Gif of my game

<img src = "assets/eae/Final/final.gif">

## Game Concept and Features

My final game is a two-player racing game where players compete to reach the finish line first while avoiding obstacles along the track.

- **Player 1 Controls**: Uses the keyboard with WASD keys for up, down, left, and right movement.
- **Player 2 Controls**: Uses a game controller, navigating with the left joystick for directional movement.
- **Obstacles**: Each player’s lane contains rocks that appear dynamically. Players must avoid these obstacles to maintain their speed and stay ahead of their opponent.
- **Game Objective**: The first player to cross the finish line is declared the winner.

I chose to develop this game because competitive multiplayer games are highly engaging and create a fun and interactive experience.

## Experience with Classmate's System and Code

I worked with Liu Yan's **Collision System** to handle obstacle interactions in my game. Here are my thoughts on integrating their system into my project:

- **Ease of Integration**: The integration process was relatively straightforward. Liu Yan's system had clear documentation and was modular enough to plug into my engine with minimal adjustments.
- **Interface Usability**: The interface was intuitive and easy to use. The collision detection events were easy to hook into my gameplay logic, making it seamless to implement speed penalties for colliding players.
- **What I Learned**: Working with Liu Yan's system gave me a better understanding of how collision detection is implemented in game engines. I particularly appreciated how the system decouples collision detection from gameplay, making it versatile for different types of games.
- **Suggestions**: One improvement could be adding more examples or usage cases in the documentation to help users quickly understand how to customize the system for unique scenarios.

## Reflection on the Semester

Throughout the semester, I learned valuable lessons about game engine design, systems integration, and the importance of well-structured architecture.

#### Goals of the Assignments

I believe the goal of the assignments was to teach us:

1. How to build modular and reusable systems.
2. The importance of designing clean interfaces for easier integration.
3. How to think critically about system dependencies and ensure they are loosely coupled.

#### Personal Insights

- **Key Takeaways**: I gained a deeper appreciation for the complexities of game engine architecture and how small design decisions can have a big impact on maintainability and flexibility. For instance, when implementing the input system, I learned to prioritize extensibility to support multiple device types without significant rewrites.
- **Challenges and New Perspectives**: Before this class, I hadn’t considered the importance of planning for edge cases, like how systems might interact under unexpected conditions. Now, I view engineering as both a creative and logical discipline, where anticipation of future use cases is critical.

#### Thoughts on Engineering, Architecture, and Design

- **Design Philosophy**: I now lean towards spending more time upfront designing flexible systems rather than iterating as I go. This approach reduces technical debt and saves time in the long run, especially for larger projects.
- **Good Architecture**: In my opinion, good software architecture is modular, scalable, and well-documented. It anticipates future requirements and isolates components to prevent unintended side effects during changes. Bad architecture, on the other hand, is tightly coupled, hard to understand, and inflexible to new features.

#### Final Thoughts

This class has reshaped my approach to software development, particularly in understanding the trade-offs between flexibility and simplicity. It has been a challenging but rewarding experience that will influence how I approach future projects in game development.