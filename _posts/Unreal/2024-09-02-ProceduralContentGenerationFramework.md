---
layout:       post
title:        "Unreal程序化自动生成地图（PCG）"
author:       "Caroline飘小蝎"
header-style: text
catalog:      true
tags:
    - PCG
    - Unreal Engine
    - Chinese
---

参考资料：

[Unreal5.2 程序化自动生成合集](https://space.bilibili.com/355571550/channel/collectiondetail?sid=1331617)

[UE5_PCG和Landscape配合](https://www.bilibili.com/video/BV1Hk4y137Y6/?spm_id_from=333.337.search-card.all.click)

## 插件应用

<img src="\assets\Unreal\PCG\P1\1.png" style="zoom:80%;" />



## 地形表面采样

**PCG Volume**：程序化生成的范围体积

<img src="\assets\Unreal\PCG\P1\2.png" style="zoom:50%;" />

**PCG Graph**：PCG 贴图

<img src="\assets\Unreal\PCG\P1\3.png" style="zoom:80%;" />

### Surface Sampler

需要打开Surface Sampler的Debug模式

<img src="\assets\Unreal\PCG\P1\4.png" style="zoom:50%;" />

创建好地形后Generate PCG Volume即可得到采样点，颜色代表深度（density）

<img src="\assets\Unreal\PCG\P1\5.png" style="zoom:50%;" />

<img src="\assets\Unreal\PCG\P1\6.png" style="zoom:80%;" />

参数：

- **Points Per Squared Meter**：每平方米的采样点数量
- **Looseness**：采样点之间的边界大小
- **Seed**：随机数种子，改变每个点的density
- **Unbounded**：不局限，在整个地图生成
- Density：黑色为0，白色为1

### TransformPoints

<img src="\assets\Unreal\PCG\P1\7.png" style="zoom:80%;" />

参数：

<img src="\assets\Unreal\PCG\P1\8.png" style="zoom:80%;" />

效果：

<img src="\assets\Unreal\PCG\P1\9.png" style="zoom:50%;" />

### StaticMeshSpawner

<img src="\assets\Unreal\PCG\P1\10.png" style="zoom:80%;" />

- **Weight**：权重

在MeshEntries中添加三个StaticMesh作为程序化生成的物体：

<img src="\assets\Unreal\PCG\P1\11.png" style="zoom:80%;" />

效果：

<img src="\assets\Unreal\PCG\P1\12.png" style="zoom:50%;" />
