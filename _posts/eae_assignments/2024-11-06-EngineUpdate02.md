---
layout:       post
title:        "Game Engine Update 02"
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

This week, I focused on enhancing my player input system by adding controller support:

Below is a GIF demonstrating the new controller functionality in my game:

<img src="\assets\eae\assignment10\assignment10.gif" style="zoom:100%;" />

## SDL import

To enable controller support, I integrated SDL (Simple DirectMedia Layer) into the project.

SDL is a cross-platform development library that provides low-level access to essential hardware components such as audio, keyboard, mouse, joystick, and graphics through OpenGL and Direct3D. After downloading the development version, I added it to the "External" folder within my solution. I then configured the include paths and library directories in Visual Studio, successfully enabling SDL for the player input system.

<img src="\assets\eae\assignment10\1.png" style="zoom:50%;" />

<img src="\assets\eae\assignment10\2.png" style="zoom:50%;" />

## System Variable Configuration

To ensure the program runs correctly, it’s essential to configure the location of `SDK.dll` in the system variables. Without this setting, the game will throw an error upon startup.

<img src="\assets\eae\assignment10\3.png" style="zoom:50%;" />

## Controller Logic Implementation

**Left Stick Controls Object Movement**

Moving the left stick in any direction (forward, backward, left, or right) will cause the in-game object to move accordingly.

**Right Stick Controls Camera Movement**

The right stick controls the camera, allowing it to shift forward, backward, left, or right as the stick is moved in each direction.

**A Button Switches Object Mesh**

Pressing the A button will switch the mesh of the first object to the mesh of the second object.

**B Button Exits the Game**

Pressing the B button will exit the game.
