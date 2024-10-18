---
layout:       post
title:        "Game Engine II Assignment07"
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

<img src="\assets\eae\assignment7\RecordingAssignment7.gif" style="zoom:50%;" />

## MayaMeshExporter references and dependencies

I think that the MayaMeshExporter does not depend on or reference any other projects within this context. It is designed to be a self-contained module that can be built independently. This means that all necessary functionality for exporting meshes from Maya is encapsulated within the MayaMeshExporter project itself, without requiring external dependencies. This design choice enhances modularity and allows for easier maintenance and integration into other projects as needed.

## Unused data

 *I chose not to export the unused data (normals, tangents, bitangents, texture coordinates) to my human-readable file. My reasoning is as follows:*

- **Simplified Structure**: By omitting unused data, the exported file remains more readable and easier to debug.
- **Performance Considerations**: Reducing the amount of data exported helps in optimizing loading times without sacrificing essential mesh details.

## Screenshot of plug-in debugging

<img src="\assets\eae\assignment7\1.png" style="zoom:50%;" />

In the image above, you can see Visual Studio attached to my plug-in. The yellow arrow indicates that my plug-in is loaded and its symbols are available for debugging.

## Handling Models with Too Many Vertices

*If I attempt to load a model with too many vertices, the code gracefully handles this situation instead of crashing or rendering incorrectly.*

- **Error Logging**: If the limit is exceeded, an error message is logged, and the user is notified rather than causing a crash.

<img src="\assets\eae\assignment7\2.png" style="zoom:50%;" />
