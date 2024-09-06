---
layout:       post
title:        "Unreal Game Ability System (GAS)"
author:       "Caroline飘小蝎"
header-style: text
catalog:      true
tags:
    - GAS
    - Unreal Engine
    - Chinese
---

参考资料：

- [UE5.3 GAS](https://www.bilibili.com/video/BV1Jx4y1Z7ig/?p=2&vd_source=1144610de5ae0bf9c26dfc9f98e02f2f)

## 学习大纲

<img src="\assets\Unreal\GAS\1.png" style="zoom:50%;" />

## 插件应用

<img src="\assets\Unreal\GAS\2.png" style="zoom:80%;" />

并在Build.cs中增加插件依赖：

```c++
PublicDependencyModuleNames.AddRange(new string[] { "Core", "CoreUObject", "Engine", "InputCore", "GameplayAbilities", "GameplayTags", "GameplayTasks" });
```



## 基础

### 技能  AbilitySystemComponent (ASC)

以英雄联盟为例：

- Lv
- Gameplay Effect (GE)
  - 消耗
    - HP, MP, Strength
  - 伤害
    - 魔法，物理
- Gameplay Cue (Cue)
  - 特效
  - 声音
- Gameplay Task
  - 效果（击飞等等）
- Gameplay Tag (Tag)
  - 技能之间的相互影响（优先级打断）

### 属性 Gameplay Attribute (GA)

以英雄联盟为例：

- HP
- MP
- 冷却速度
- 移动速度
- ...

### 项目配置

- 在Project Settings中关闭自动曝光（Auto Exposure）
- 创建BaseCharacter (C++), BP_BaseCharacter, BP_Player, BP_Enemy, BP_GameMode, BP_PlayerController
- 在BP_Player中新增SpringArm和Camera

## 基本角色与相机控制
