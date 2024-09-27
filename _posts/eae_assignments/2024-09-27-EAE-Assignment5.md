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

```c++
void GameObject::SubmitDataForRendering(const float i_elapsedSecondCount_sinceLastSimulationUpdate)
{
    cRenderableObject::SubmitForRendering(m_mesh,m_effect);
    Graphics::UpdateDrawCall(RigidBodyState.PredictFutureTransform(i_elapsedSecondCount_sinceLastSimulationUpdate));
}
```

**`cRenderableObject::SubmitForRendering(m_mesh, m_effect)`**:

- This utilizes the `SubmitForRendering` method from the base class (`cRenderableObject`) to pass rendering-specific data, such as `m_mesh` and `m_effect`, to the graphics system. This abstraction makes it easy for the game programmer to specify what mesh and effect (shader) to use when rendering the game object, without having to deal with lower-level graphics API details.

**`Graphics::UpdateDrawCall(RigidBodyState.PredictFutureTransform(i_elapsedSecondCount_sinceLastSimulationUpdate))`**:

- This ensures that the graphics system is updated with the object's predicted transform, which is calculated using the `RigidBodyState`. The `PredictFutureTransform` function takes into account the time elapsed since the last simulation update, providing a smooth transition and preventing visual stuttering or snapping that might occur if the graphics and physics systems were not synchronized.

## The size of data needed for each draw call

```c++
struct sDataRequiredToRenderAFrame
{
	sColor background_color;
	eae6320::Graphics::ConstantBufferFormats::sFrame constantData_frame;
	std::vector<std::pair<eae6320::Graphics::cMesh*&, eae6320::Graphics::cEffect*&>> mesh_effect_pairs;
	std::vector<eae6320::Graphics::ConstantBufferFormats::sDrawCall> constantData_drawcalls;
};
```

- Each draw call in `mesh_effect_pairs` adds **16 bytes** per pair.
- Each draw call in `constantData_drawcalls` adds **64 bytes**.

The actual memory requirements for each draw call would be influenced by the number of elements stored in the `mesh_effect_pairs` and `constantData_drawcalls` vectors. 

## Why extrapolation/prediction is necessary

During each frame render, the graphics system uses the most recent simulation data to predict where objects should be, based on their current velocity, acceleration, or other properties. This is done by calculating the position of each object at a future point in time, relative to the last simulation update.

Extrapolation is necessary in rendering with your engine to handle the discrepancy between simulation update rates and rendering rates. By predicting future positions of objects based on their current state, the engine ensures **smooth transitions and consistent visuals**, even when the simulation and rendering do not run at the same frequency. This results in a more polished and responsive visual experience for players.
