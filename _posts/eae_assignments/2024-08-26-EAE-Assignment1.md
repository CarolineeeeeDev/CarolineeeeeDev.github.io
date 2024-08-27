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

 [LehanLi_assignment01_opengl.zip](\assets\eae\assignment1\LehanLi_assignment01_opengl.zip) 

## GIF of MyGame

<img src="\assets\eae\assignment1\Gif for assignment01.gif" style="zoom:50%;" />

## Generated Log File

<img src="\assets\eae\assignment1\2.png" alt="2" style="zoom:70%;" />

## Process of Completing Assignment01

### Overview

I think the purpose of Assignment 01 is to understand the structure of the solution, create and integrate a static graphics library, and explore shader programming while ensuring cross-platform consistency. The assignment also emphasizes the importance of following best practices in version control. Below is a detailed account of how I completed the assignment.

### 1. Implement Graphics Library

I began by creating a **static library project** under the Engine filter, using the files provided. To ensure platform-specific files were correctly organized and set to build only with the appropriate configuration, I modified the `Excluded from Build` property for files under the "Direct3D" and "OpenGL" filters on each platform.

<img src="\assets\eae\assignment1\1.png" alt="1" style="zoom:50%;" />

Additionally, I configured the path for the `Forced Include File`in the Graphics project to ensure both Direct3D and OpenGL would function correctly.

### 2. Set references and correct build orderss

I ensured that all necessary references were added, and the build order was correct. This step was crucial in making sure that the projects were properly linked and would build in the correct sequence.

### 3. Get my personal game project working

After copying and modifying the configurations of the example game project, I successfully set up my personal game project, which displayed a white triangle upon startup.

To animate the triangle's color, I added code in the `animatedColor.shader` file. By using `sin` and `cos` functions to update the values of `o_color.r`, `o_color.g`, and `o_color.b`, I created a dynamic color change in real-time.

### 4. Modify cMyGame.h configuration

I customized my game’s window name and class name in the `cMyGame.h` file and set the **EAEALIEN** icon as my game’s icon.

<img src="\assets\eae\assignment1\3.png" alt="3" style="zoom:50%;" />

### 5. Add logging messages

To track the game's initialization and cleanup processes, I added the **`OutputMessage`** function from the Logging class to the `Initialize` and `CleanUp` functions in `cMyGame.cpp`. This logging ensured that important events were recorded, aiding in debugging and tracking the game’s lifecycle.

## Optional Challenges

I implemented additional game modes by using the **`SetSimulationRate`** function defined in the `iApplication` class and capturing real-time keyboard input in `cMyGame.cpp`. This allowed me to create several modes for my game:

- **Fast Mode**: Activated by pressing the "Up" key.
- **Slow Mode**: Activated by pressing the "Down" key.
- **Pause Mode**: Activated by pressing the "Space" key.
- **Regular Mode**: Restored by releasing all keys.


The point of doing this is to set different **`m_simulationRate`** value:

| m_simulationRate | Game Mode    |
| ---------------- | ------------ |
| 0                | Pause Game   |
| 0~1              | Slow Mode    |
| 1                | Regular Mode |
| 1+               | Fast Mode    |

## Thoughts About the Engine Code Base

The engine’s code is organized into distinct modules, each responsible for specific functions such as receiving user input or printing debug information. These modules are integrated using add references. I find this structure to be very clear, which facilitates iterative development and error debugging.

The code style is also commendable, with well-organized naming conventions for variables and functions, and low coupling between components, making the codebase both readable and maintainable.

Initially, I was confused by the dependencies between projects and the build order, which hindered my ability to generate the game correctly. However, after attending class and understanding the explanations, I was able to resolve these issues.

## My Expectations

Through this assignment, I have gained a deeper understanding of the structure of game project files and the interaction between game projects and the engine’s source code. I hope this course will further enhance my knowledge of fundamental game engine development concepts, such as implementing sound and physics systems.

### Time cost

I spent approximately 8 hours on this project, with the majority of the time dedicated to understanding and correctly setting the build order.