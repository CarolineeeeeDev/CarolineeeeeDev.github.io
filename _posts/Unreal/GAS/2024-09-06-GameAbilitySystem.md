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

<img src="\assets\Unreal\GAS\1.png" style="zoom:60%;" />

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

### 角色控制

角色移动、转向、跳跃

<img src="\assets\Unreal\GAS\3.png" style="zoom:80%;" />

将第一人称控制模式转换为第三人称控制：

- BP_Player：取消勾选Use Controller Rotation Yaw

- SpringArm：勾选Use Pawn Control Rotation
- CharacterMovement：勾选Orient Rotation to Movement

### 相机锁定模式和夹角限制

在BP_Player中限制夹角

<img src="\assets\Unreal\GAS\4.png" style="zoom:80%;" />

相机视角锁定与非锁定设置

<img src="\assets\Unreal\GAS\5.png" style="zoom:80%;" />

### 平A与移动动画制作

动画制作：创建BlendSpace和AnimationBlueprint

**BS_Walk**

<img src="\assets\Unreal\GAS\6.png" style="zoom:60%;" />

<img src="\assets\Unreal\GAS\7.png" style="zoom:80%;" />

**ABP_Sinbi**

<img src="\assets\Unreal\GAS\8.png" style="zoom:60%;" />

Event Graph:

<img src="\assets\Unreal\GAS\9.png" style="zoom:80%;" />

Anim Graph:

<img src="\assets\Unreal\GAS\10.png" style="zoom:50%;" />

创建状态机StateMachine

<img src="\assets\Unreal\GAS\11.png" style="zoom:50%;" />

Idle/Jog：

<img src="\assets\Unreal\GAS\12.png" style="zoom:50%;" />

JumpStart：

<img src="\assets\Unreal\GAS\13.png" style="zoom:50%;" />

JumpLoop：

<img src="\assets\Unreal\GAS\14.png" style="zoom:50%;" />

JumpEnd：

<img src="\assets\Unreal\GAS\15.png" style="zoom:50%;" />

Idle/Jog to JumpStart

<img src="\assets\Unreal\GAS\16.png" style="zoom:50%;" />

JumpStart to JumpLoop

<img src="\assets\Unreal\GAS\17.png" style="zoom:50%;" />

JumpLoop to JumpEnd

<img src="\assets\Unreal\GAS\18.png" style="zoom:50%;" />

JumpEnd to Idle/Jog

<img src="\assets\Unreal\GAS\19.png" style="zoom:50%;" />

创建蒙太奇 Montage

**MA_MeleeAttack**

<img src="\assets\Unreal\GAS\20.png" style="zoom:50%;" />

在BP_BaseEnemy中创建CustomEvent

<img src="\assets\Unreal\GAS\21.png" style="zoom:50%;" />

再在PlayerController中调用这个Event

<img src="\assets\Unreal\GAS\22.png" style="zoom:60%;" />

目前存在的问题：边走边平A的时候腿部不动，非常违和

解决方法：动作融合

### 动画融合

ABP_Sinbi

<img src="\assets\Unreal\GAS\23.png" style="zoom:60%;" />

并在Layered Blend per bone设置：

<img src="\assets\Unreal\GAS\24.png" style="zoom:60%;" />

但存在问题：效果像是在腰部被切断一样

解决方法：在前几帧将动画控制权交给未融合的Montage

在脚离地及落地的时候分别**Add Notify**，对应StartMontage和EndMontage

<img src="\assets\Unreal\GAS\25.png" style="zoom:60%;" />

在ABP_Sinbi的Event Graph中增加是否需要Move蒙太奇的设置

<img src="\assets\Unreal\GAS\26.png" style="zoom:60%;" />

在AnimGraph中实现是否需要Move蒙太奇的切换实现

<img src="\assets\Unreal\GAS\27.png" style="zoom:60%;" />

## 创建一个平A及CD

### 添加AbilitySystemComponent和GameplayAbility基类

在BP_BaseCharacter上新增Ability System这个Component

创建GAB_BaseAbility（父类是GameAbility）以及GAB_MeleeAttack（父类是GAB_BaseAbility），并给后者增加标签

<img src="\assets\Unreal\GAS\28.png" style="zoom:40%;" />

### GAS结合gameplay的做法

在BP_BaseCharacter中新增触发技能函数ActivateAbility，并在Gameplay Tag Container中配置所有的Tag

<img src="\assets\Unreal\GAS\29.png" style="zoom:60%;" />

在BP_BaseCharacter开始的时候执行GiveAbility

<img src="\assets\Unreal\GAS\30.png" style="zoom:40%;" />

<img src="\assets\Unreal\GAS\31.png" style="zoom:40%;" />

在GAB_MeleeAttack中实现蒙太奇的播放

<img src="\assets\Unreal\GAS\33.png" style="zoom:50%;" />

注意：子类BP_Player的BeginPlay一定要继承父类的方法（即GiveAbility），否则动画无法正常生效

<img src="\assets\Unreal\GAS\32.png" style="zoom:40%;" />

### CD设置

新增GE_MeleeCD（父类是GameEffect）并配置0.5s的CD时间

<img src="\assets\Unreal\GAS\34.png" style="zoom:50%;" />

注意还需要在GAB_MeleeAttack中提交CD

<img src="\assets\Unreal\GAS\35.png" style="zoom:50%;" />

### 平A检测打到谁了
