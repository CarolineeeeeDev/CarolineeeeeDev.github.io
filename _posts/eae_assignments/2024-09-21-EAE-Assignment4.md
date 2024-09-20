---
layout:       post
title:        "Game Engine II Assignment04"
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

## Download Link

 [LehanLi_assignment04_direct3d.zip](\assets\eae\assignment4\Assignment04_d3d.zip) 

 [LehanLi_assignment04_opengl.zip](\assets\eae\assignment4\Assignment04_OpenGl.zip) 

## GIF of MyGame

<img src="\assets\eae\assignment4\Assignment04.gif" style="zoom:50%;" />

- When I press "left arrow key", the second mesh will not be drawn.
- When I press "right arrow key", the second mesh will be bind to the animated color effect.

## Three screenshots of my game running

**default state:**

<img src="\assets\eae\assignment4\1.png" style="zoom:50%;" />

**missing a mesh:**

<img src="\assets\eae\assignment4\2.png" style="zoom:50%;" />

**a mesh using a different effect:**

<img src="\assets\eae\assignment4\3.png" style="zoom:50%;" />

## The code that submits the background color

<img src="\assets\eae\assignment4\4.png" style="zoom:80%;" />

## The code that submits a mesh/effect pair to be drawn

<img src="\assets\eae\assignment4\5.png" style="zoom:80%;" />

## Why we have to submit things this way

Many modern engines separate the simulation and rendering processes onto different threads to increase performance. The rendering thread is often ahead of the simulation thread, so caching all the data that needs to be rendered for the current frame enables better parallel processing. The rendering thread can focus on taking the cached data, sending it to the GPU, and processing it, while the simulation thread continues updating game logic independently.

## The sizeof(cMesh) in both platforms

- x64: 32
- x86: 16

**data members:**

<img src="\assets\eae\assignment4\6.png" style="zoom:80%;" />

The vertex and index buffers are essential components for rendering a mesh. Each graphics API (Direct3D, OpenGL, etc.) requires platform-specific buffer objects to store vertices and indices. These buffers are necessary for rendering triangles efficiently and cannot be removed or downsized without breaking the functionality.The platform-specific data members are already conditionally compiled using `#ifdef` preprocessor directives, meaning only the relevant data members are included based on the target platform (Direct3D or OpenGL). This is an efficient approach because it avoids unnecessary memory usage on platforms where certain members aren’t needed.

## The sizeof(cEffect) in both platforms

- x64: 56
- x86: 20

**data members:**

<img src="\assets\eae\assignment4\7.png" style="zoom:80%;" />

This class, `cEffect`, cannot be meaningfully reduced in size without compromising functionality or performance.The current member variables are already laid out efficiently for most architectures. Pointers (such as `m_vertexShader` and `m_fragmentShader`) are likely aligned optimally for the system, ensuring no unnecessary padding is introduced. While slight reordering might theoretically reduce padding, the potential gains would be marginal and platform-specific. Any attempt to reduce memory usage further by reordering the members would risk breaking alignment requirements and could lead to performance penalties on certain hardware.

## Optional Challenges

