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

This uses the sine function (`std::sin`) to generate smoothly varying values between 0 and 1 for each color channel. Once the red, green, and blue values are calculated, they are submitted to the graphics engine by calling `Graphics::SubmitBackgroundColor`. In the `SubmitBackgroundColor` function, the submitted color is written into a shared data structure that the rendering system uses.

## The code that submits a mesh/effect pair to be drawn

<img src="\assets\eae\assignment4\5.png" style="zoom:80%;" />

The function `eae6320::Graphics::BindEffectToMesh(cMesh*& mesh, cEffect*& effect)` handles submitting a mesh and effect pair to the rendering system. After the null checks, it accesses `s_dataBeingSubmittedByApplicationThread`, which is a shared data structure used to store data submitted by the application thread for rendering. This data will be processed by the rendering thread later.

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

## Total memory of my Graphics project's data to render frames

Total memory = 176*2 = **352**

<img src="\assets\eae\assignment4\8.png" style="zoom:80%;" />

**1. background_color:**

This represents the color data used for rendering the background (RGBA color values).

Assuming `sColor` consists of 4 floating-point values (one each for `r`, `g`, `b`, and `a`), and each floating-point value (i.e., `float`) is 4 bytes:

- **Memory for background_color** = 4 (components: r, g, b, a) * 4 bytes = **16 bytes**

**2. constantData_frame:**

This is likely a constant buffer that stores data needed for every frame, such as transformation matrices (view, projection), lighting parameters, or other frame-specific information. 

This can vary based on the actual data being stored in the `sFrame` constant buffer format.

**3. mesh_effect_pairs:**

This vector stores pairs of references to `cMesh` and `cEffect` objects that need to be rendered for each frame.

The memory usage here depends on:

- **Number of mesh/effect pairs**.
- **Size of each pair**: Each pair contains two references, one to a `cMesh*` and one to a `cEffect*`. References are typically the same size as pointers (4 bytes on 32-bit systems, 8 bytes on 64-bit systems).
