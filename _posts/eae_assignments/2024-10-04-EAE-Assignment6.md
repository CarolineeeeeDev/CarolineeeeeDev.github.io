---
layout:       post
title:        "Game Engine II Assignment06"
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

## The advantages of having human-readable asset files

Human-readable asset files offer several advantages that benefit both developers and artists working on a project. One of the most significant advantages is the ease of debugging. When something in the game doesn't render correctly, being able to quickly open an asset file and inspect its data is invaluable. This reduces the time spent tracing issues back to their source and allows for quick fixes when the problem is with the content rather than the code.

Additionally, human-readable files are much easier to maintain. As games evolve, asset formats may need to change or adapt, and with clear formatting and logical structures, it’s easier to update or expand upon existing data. Human-readable files also foster collaboration, as more people can understand the contents of a file without needing specialized tools or extensive documentation.

Another key advantage is flexibility. In situations where specific tools are unavailable or malfunctioning, human-readable formats allow for manual editing, testing, and experimentation.

## My mesh files

Here is an example of one of my mesh files (square.lua):

```lua
return { 
    vertexData = {
        {0.0, 0.0, 0.0},
        {1.0, 0.0, 0.0},
        {1.0, 1.0, 0.0},
        {0.0, 0.0, 0.0},
        {1.0, 1.0, 0.0},
        {0.0, 1.0, 0.0}
    },
    shapeCount = 2,
    vertexCountPerShape = 3
}
```

This file specifies a mesh consisting of two triangular shapes, defined by six vertices. The vertex data is stored in a straightforward array, each containing three values representing the position of each vertex in 3D space.

I designed this file with human readability as a priority. The vertex data is structured as a simple array, where each set of three numbers represents a vertex’s position in 3D space. By using an array, I can maintain the order of the vertices, which is important for defining the shapes correctly.

Each shape is composed of three vertices, and I’ve explicitly included the number of shapes (`shapeCount`) and the number of vertices per shape (`vertexCountPerShape`). This makes it easier to understand how the mesh is structured at a glance. Although this information could be deduced from the vertex data itself, including it explicitly improves clarity when debugging or reading through the file.

## Screenshot of my game

<img src="\assets\eae\assignment6\1.png" style="zoom:50%;" />

## Screenshot of my debugging MeshBuilder program

<img src="\assets\eae\assignment6\2.png" style="zoom:50%;" />
