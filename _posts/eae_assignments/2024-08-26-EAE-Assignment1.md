---
layout:       post
title:        "Game Engine II Assignment01"
author:       "Caroline飘小蝎"
header-style: text
catalog:      true
tags:
    - EAE
    - Assignment
    - C++
    - Game Engine
---

## Download Link

 [LehanLi_assignment01_direct3d.zip](\assets\eae\assignment1\LehanLi_assignment01_direct3d.zip) 

## GIF of MyGame

<img src="\assets\eae\assignment1\Gif for assignment01.gif" style="zoom:50%;" />

## Generated Log File

<img src="\assets\eae\assignment1\2.png" alt="2" style="zoom:70%;" />

## Process of Completing Assignment01

I think the point of Assignment01 is to ..

### 1. Implement Graphics Library

I created a new **static library project** under the Engine filter with files provided. By **modifying the "Excluded from build" property value** of files under "Direct3D" and "OpenGL" filters on both platforms separately, I made sure that I have the platform-specific files organized correctly, and that they are set to only build with the appropriate configuration.

<img src="\assets\eae\assignment1\1.png" alt="1" style="zoom:50%;" />

​								platform-specific files (under x64)

Then to ensure Direct3D and OpenGL works well, I also set the path of Forced Include File of the Graphics.

### 2. Set references and correct build orders



### 3. Get my personal game project working

After copying and modifying configurations of the example game project, my game project works well as it shows a white triangle when the game starts. 

To make animations...



## Optional Challenges

By using the **SetSimulationRate** function defined in iApplication class and getting realtime keyboard input in "cMyGame.cpp", I created several modes for my game:

Press "Up" key: **Fast mode**;

Press "Down" key: **Slow mode**;

Press "Space" key: **Pause the game**;

Release all keys: **Regular mode**.

The point of doing this is to set different **m_simulationRate** value:

| m_simulationRate | Game Mode    |
| ---------------- | ------------ |
| 0                | Pause Game   |
| 0~1              | Slow Mode    |
| 1                | Regular Mode |
| 1+               | Fast Mode    |

## Thoughts About the Engine Code Base



## My Expectations