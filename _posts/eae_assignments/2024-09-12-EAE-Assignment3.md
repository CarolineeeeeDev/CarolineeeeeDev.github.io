---
layout:       post
title:        "Game Engine II Assignment03"
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

 [LehanLi_assignment03_direct3d.zip](\assets\eae\assignment3\LehanLi_Assignment03_D3D.zip) 

 [LehanLi_assignment03_opengl.zip](\assets\eae\assignment3\LehanLi_Assignment03_OpenGL.zip) 

## GIF of MyGame

<img src="\assets\eae\assignment3\Assignment03.gif" style="zoom:50%;" />

## How I made Graphics.cpp platform-independent

I created a **cView** class and implemented some interfaces such as: **ClearBuffers, InitializeViews and CleanUp**. Then I implemented these functions in cView.d3d.cpp and cView.gl.cpp.

I also created an interface called **SwapBuffer** in **sContext** class for different platform to swap content from back buffer to front buffer. Then I implemented it in sContext.d3d.cpp and sContext.gl.cpp.

Then for the content that is the same in d3d and gl platform, I just move them into Graphics.cpp.

## The code that clears the back buffer color

I used the s_view_ClearBuffers(0.0f, 0.0f, 0.0f) to clear the back buffer color. Then I changed the parameters to rgb values to make animated color for the background.

<img src="\assets\eae\assignment3\1.png" style="zoom:100%;" />

## The screenshot of my game with a different background color

<img src="\assets\eae\assignment3\2.png" style="zoom:50%;" />

## The code that initializes an effect

<img src="\assets\eae\assignment3\3.png" style="zoom:100%;" />

I used **Vertex Shader Path** and **Fragment Shader Path** as parameters to initialize an effect.

## Memory a single effect takes up in both platforms

- **x64:** 48
- **x86:** 16

<img src="\assets\eae\assignment3\5.png" style="zoom:100%;" />

## The code that initializes a mesh 

<img src="\assets\eae\assignment3\6.png" style="zoom:100%;" />

I used **TriangleCount**, **VertexCountPerTriangle** and **VertexData** as parameters to initialize a mesh.

## Memory a single mesh takes up in both platforms

- **x64:** 24
- **x86:** 12

<img src="\assets\eae\assignment3\4.png" style="zoom:100%;" />



## Optional Challenges

