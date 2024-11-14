---
layout:       post
title:        "Engine System Write Up"
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

### **Overview of the Player Input System**

The player input system is a crucial part of the game engine, allowing developers to manage player actions and controls efficiently. It replaces the older input system, offering a more flexible and customizable way to handle keyboard, mouse, and controller inputs. Key features include input mapping, customizable actions, real-time event processing, and configuration of input sensitivity and dead zones.

### **Project Functionality**

The updated input system enables the following:

1. **Input Mapping and Customizable Actions**:

   - Players can define specific inputs (like WASD or arrow keys) to control character movement.

   - Game-specific actions, such as "Jump," "Shoot," or "Interact," can be mapped to any key or controller button.

     <img src="\assets\eae\assignment11\1.png" style="zoom:50%;" />

2. **Enhanced Player and Camera Control**:

   - Input states are tracked frame-by-frame, ensuring responsive and smooth interactions.
   - Player and camera positions are updated in real-time based on user inputs, ensuring a consistent and immersive gameplay experience.

3. **Controller Integration**:

   - SDL (Simple DirectMedia Layer) has been integrated for controller support, with functions to handle joystick inputs for object movement and camera control.

   - Additional features allow switching object meshes and exiting the game through designated buttons.

     <img src="\assets\eae\assignment10\assignment10.gif" style="zoom:50%;" />

### **Instructions to Use the Project**

To integrate the player input system into your own game projects, follow these steps:

1. **Download and Setup**:

   - Download the provided ZIP file containing the code.
   - Extract the files and add the static library project to your solution for the engine.

2. **System Variable Setup**:

   - Ensure the correct location of `SDK.dll` is set in your system variables to avoid errors during startup.
   - Configure Visual Studio's include paths and library directories to accommodate the SDL integration if using controller support.

   <img src="\assets\eae\assignment10\3.png" style="zoom:50%;" />

3. **Integration in Your Game Loop**:

   - Utilize methods like `IsActionPressed("Jump")` or `GetAxis("Move")` to handle input queries during gameplay.
   - Update player and camera positions based on the input states retrieved from the `InputManager`.

### **Application of Course Knowledge**

Throughout the project, I applied multiple concepts learned this semester, including:

- **Input Handling**: Reworked the previous user input system using key concepts like state tracking and input mapping for better user customization.
- **Real-Time Updates**: Focused on frame-by-frame input processing, ensuring the game responded smoothly to user actions.
- **Integration of External Libraries**: Learned how to integrate SDL, configuring include paths, library directories, and handling external dependencies.

### **Challenges and Interesting Learnings**

1. **Event Precision Management**:
   - Ensuring that key press, release, and hold events triggered correctly without delay was challenging, particularly when dealing with simultaneous key presses.
   - I had to fine-tune the update loop to handle multiple input states accurately.
2. **Controller Integration with SDL**:
   - Integrating SDL was a learning curve, requiring configuration changes in Visual Studio and system variables.
   - Handling controller-specific nuances, like joystick dead zones and analog sensitivity, presented additional challenges.
3. **Flexible Key Binding and Dynamic Reloading**:
   - Designing a system that allows dynamic key binding changes without requiring a code update was a rewarding challenge.
   - This flexibility will be beneficial for other students, enabling them to adapt the input system to different game genres easily.

### **Download and Instructions**

A ZIP file containing the source code, the static library project for the runtime engine, and the executable for the asset builder is available [here](#). Below are instructions on setting it up:

1. **Download the ZIP file** and extract it to your project directory.
2. **Add the static library project** to your solution.
3. **Set up path variables**.

<img src="\assets\eae\assignment11\2.png" style="zoom:50%;" />

1. **Follow the input configuration guide** included in the write-up to set up your game's specific input needs.
2. **Test and adjust** sensitivity settings, dead zones, and key bindings to fit your project requirements.

By following these steps, you should be able to utilize the player input system effectively in your final game projects. For any additional guidance, feel free to consult the in-code comments or reach out for support.
