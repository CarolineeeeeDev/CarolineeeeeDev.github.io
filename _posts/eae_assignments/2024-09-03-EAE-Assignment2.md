---
layout:       post
title:        "Game Engine II Assignment02"
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

 [LehanLi_assignment02_direct3d.zip](\assets\eae\assignment2\LehanLi_assignment02_direct3d.zip) 

 [LehanLi_assignment02_opengl.zip](\assets\eae\assignment2\LehanLi_assignment02_opengl.zip) 

## GIF of MyGame

<img src="\assets\eae\assignment2\Assignment02.gif" style="zoom:50%;" />

## Screenshots from a Direct3D GPU Capture

<img src="\assets\eae\assignment2\1.png" style="zoom:100%;" />

<img src="\assets\eae\assignment2\2.png" style="zoom:100%;" />

## Screenshots from an OpenGL GPU Capture

<img src="\assets\eae\assignment2\3.png" style="zoom:100%;" />

<img src="\assets\eae\assignment2\4.png" style="zoom:100%;" />

<img src="\assets\eae\assignment2\5.png" style="zoom:100%;" />

## The Code That Binds the Effect and Draws the Mesh

<img src="\assets\eae\assignment2\6.png" style="zoom:50%;" />

## Process of Completing Assignment02

### Overview

In this assignment, the goal was to encapsulate platform-specific code in a clean, reusable way by creating `cMesh` and `cEffect` classes. These would abstract platform-specific data and functions while maintaining a platform-independent interface. This also introduced the idea of organizing rendering assets in a modular way, allowing for future scalability and maintainability as more meshes or effects get added.

### 1. Create class for mesh and effect

The first step in tackling this assignment was to create the `cMesh` and `cEffect` classes. I chose to structure them as classes to encapsulate all the necessary data and methods. The main data handled here includes vertex buffers and shaders, but split across platform-specific implementations in separate `cpp` files (e.g., `cMesh.d3d.cpp` and `cMesh.gl.cpp`).

The challenge here was deciding what parts of the code were truly platform-independent. For the mesh, most of the initialization and rendering is platform-specific because Direct3D and OpenGL handle vertex buffers differently. The `cEffect`, on the other hand, could share a bit more platform-independent logic for binding shaders, though the actual shader compilation needed to stay platform-specific.

### 2. Adding a second triangle

To add the second triangle, I updated the vertex array for both platforms, mindful of their different winding orders. In Direct3D, the left-handed system meant the second triangle needed to follow the same order as the first, while OpenGL’s right-handed system required a different approach. Initially, I missed this subtle difference and was only seeing one triangle rendered, but after debugging, I corrected the vertex order in OpenGL to render both triangles correctly.

### 3. GPU capture

I spent some time learning how to use the GPU capture tool to debug graphics problems. This helped me confirm that the correct buffers and shaders were bound during rendering. It also allowed me to trace the draw calls to ensure that two triangles were being rendered. This tool was useful for identifying where I had missed setting up the second triangle correctly in OpenGL.

## Remaining Differences

There are still some  remaining differences between Graphics.d3d.cpp and Graphics.gl.cpp.

1. **Render Target View and Depth/Stencil View**

- **Direct3D**: `s_renderTargetView` and `s_depthStencilView` are used to bind the framebuffer and depth buffer for rendering. These are specific to Direct3D's way of handling render targets and depth/stencil buffers. The code calls `CreateRenderTargetView` and `CreateDepthStencilView` for setting up these resources.
- **OpenGL**: There is no explicit render target view, as OpenGL handles this with the default framebuffer, and depth buffer is managed via `glClearDepth()`.

**Solution**: To make this platform-independent, I could abstract the framebuffer and depth buffer logic into platform-specific setup functions. These could be called from a unified cpp file, which would delegate the setup to InitializeRenderTargets() or similar platform-specific functions.

2. **Constant Buffers (Uniform Buffers)**

- **Direct3D**: Constant buffers are handled explicitly using `ID3D11Buffer` and `UpdateSubresource()` for transferring data to the GPU.
- **OpenGL**: OpenGL uses `glUniform` to update shader variables or `glBufferData` for uniform buffers.

**Solution**: Abstract the constant buffer handling into a platform-independent function like `UpdateConstantBuffer()`, with platform-specific code in `d3d` and `gl` files. The platform-independent interface would manage the API differences.

3. **Resource Creation (Textures, Buffers)**

- **Direct3D**: The creation of resources like vertex buffers, textures, and render target views is explicit, using methods such as `CreateBuffer()` and `CreateRenderTargetView()`.
- **OpenGL**: OpenGL uses `glGenBuffers()`, `glBindBuffer()`, etc., for resource creation.

**Solution**: Introduce platform-agnostic initialization functions like `CreateVertexBuffer()`. These functions would internally delegate to platform-specific implementations in `d3d` or `gl`.

## Optional Challenges

I made a house shape with 3 triangles.

<img src="\assets\eae\assignment2\7.png" style="zoom:50%;" />

| VertexIndex | VertexPosition (D3D) |
| ----------- | -------------------- |
| 0           | (-0.5, 0, 0)         |
| 1           | (0, 0.5, 0)          |
| 2           | (0.5, 0, 0)          |
| 3           | (-0.3, -0.5, 0)      |
| 4           | (-0.3, 0, 0)         |
| 5           | (0.3, 0, 0)          |
| 6           | (-0.3, -0.5, 0)      |
| 7           | (0.3, 0, 0)          |
| 8           | (0.3, -0.5, 0)       |

