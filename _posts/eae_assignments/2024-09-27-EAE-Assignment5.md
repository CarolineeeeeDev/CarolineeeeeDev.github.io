---
layout:       post
title:        "Game Engine II Assignment05"
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

 [LehanLi_assignment05_direct3d.zip](\assets\eae\assignment5\Assignment05_D3D.zip) 

 [LehanLi_assignment05_opengl.zip](\assets\eae\assignment5\Assignment05_OpenGL.zip) 

## GIF of MyGame

<img src="\assets\eae\assignment5\Assignment05.gif" style="zoom:50%;" />

- “WASD” : Control movement of one game object
- Arrow Keys : Control movement of camera
- Space Key: Switch one mesh to another

## Representation of a game object

In my design, the `GameObject` class is derived from the `cRenderableObject` class, and each class is structured to serve a specific role in the game:

```c++
class GameObject : public Graphics::cRenderableObject
{
public:
    GameObject(Graphics::cMesh* i_mesh, Graphics::cEffect* i_effect);
    ~GameObject();

    void Update(const float i_deltaTime);

    void SetPosition(const Math::sVector& i_position);
    void SetOrientation(const Math::cQuaternion& i_orientation);
    void SubmitDataForRendering(const float i_elapsedSecondCount_sinceLastSimulationUpdate);

    Physics::sRigidBodyState RigidBodyState;
};
```

```c++
class cRenderableObject
{
public:
    cRenderableObject() = default;
    cRenderableObject(Graphics::cMesh* i_mesh, Graphics::cEffect* i_effect);
    ~cRenderableObject();

    void SubmitForRendering(cMesh*& mesh, cEffect*& effect);

    void SetMesh(Graphics::cMesh* i_mesh);
    void SetEffect(Graphics::cEffect* i_effect);
    void SwitchEffect(Graphics::cEffect* i_effect);
    void SwitchMesh(Graphics::cMesh* i_mesh);
    void CleanUp();

    Graphics::cMesh* m_mesh = nullptr;
    Graphics::cEffect* m_effect = nullptr;
};
```

**`cRenderableObject` Class**:
This class is responsible for storing all data necessary for rendering. By isolating rendering-specific attributes here, the class can focus on the visual representation of the object without being concerned about other aspects like physics or game logic. This separation of responsibilities promotes a clean design that is easy to maintain and extend.

**`GameObject` Class**:
The `GameObject` class extends `cRenderableObject` to include additional functionality needed for game behavior. Specifically, it stores `RigidBodyState` data, which is used to handle movement and physics calculations for the game object. The `RigidBodyState` keeps track of properties like position, velocity, acceleration, and orientation, allowing the game to simulate realistic movement and respond to input dynamically.

## Interface being used for submitting game objects to be rendered



## The size of data needed for each draw call





## Why extrapolation/prediction is necessary

