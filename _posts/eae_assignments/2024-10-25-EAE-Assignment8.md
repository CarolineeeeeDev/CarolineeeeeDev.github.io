---
layout:       post
title:        "Game Engine II Assignment08"
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

## Binary geometry file example

<img src="\assets\eae\assignment8\1.png" style="zoom:50%;" />

The orders are as follows:

<img src="\assets\eae\assignment8\2.png" style="zoom:50%;" />

##  Advantages of Using Binary File Formats

1. **Compact Size**: Binary files are generally smaller than their human-readable counterparts since they store data in a more compact format without unnecessary overhead, leading to reduced storage requirements.
2. **Faster Load Times**: Binary formats facilitate quicker read times because they can be read directly into memory as raw bytes, eliminating the need for parsing or conversion, thus speeding up the load process at runtime.

## Comparison with Human-Readable Formats

- **Binary Formats**: Optimal for runtime performance due to compactness and speed. They are crucial when loading data frequently during gameplay, ensuring minimal delay.
- **Human-Readable Formats**: Useful for development and debugging because they can be easily edited and understood. They allow version control systems to track changes more effectively.

We use human-readable formats for data storage in source control to simplify collaboration and debugging, while binary formats are favored at runtime for performance efficiency.

## Platform-Independent Binary Files

The built binary geometry files should be the same for different platforms. Using a common abstraction layer or a middleware library that standardizes how geometry is created and stored can lead to identical binary files. The middleware handles the specifics of how to interpret the binary data for each graphics API without altering the underlying format.

## Extract data from binary file

<img src="\assets\eae\assignment8\3.png" style="zoom:50%;" />

## Error checking

<img src="\assets\eae\assignment8\4.png" style="zoom:50%;" />

## Difference between human-readable files and binary files

### size (kb)

gear.mesh (human-readable file) : **19kb**

<img src="\assets\eae\assignment8\6.png" style="zoom:50%;" />

gear.mesh (binary file) : **8kb**

<img src="\assets\eae\assignment8\5.png" style="zoom:50%;" />

### time (ms)

gear.mesh (human-readable file) : 

<img src="\assets\eae\assignment8\7.png" style="zoom:50%;" />

gear.mesh (binary file) : 

<img src="\assets\eae\assignment8\8.png" style="zoom:50%;" />

## Summary of Findings

The tests highlight the substantial advantages of using binary formats in terms of both size and loading speed. 

These findings can assist in future decisions regarding data formats for mesh files, especially when considering runtime efficiency versus development convenience.
