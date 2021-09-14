碰撞
==

本页解释了 TopDown 引擎中碰撞的工作原理。

-   [介绍](https://topdown-engine-docs.moremountains.com/collisions.html#introduction)[](https://topdown-engine-docs.moremountains.com/collisions.html#introduction)
-   [图层](https://topdown-engine-docs.moremountains.com/collisions.html#layers)[](https://topdown-engine-docs.moremountains.com/collisions.html#layers)
-   [标签](https://topdown-engine-docs.moremountains.com/collisions.html#tags)[](https://topdown-engine-docs.moremountains.com/collisions.html#tags)

介绍[](https://topdown-engine-docs.moremountains.com/collisions.html#introduction)
--------------------------------------------------------------------------------

引擎的 TopDownControllers，无论是 2D 还是 3D 版本，都是建立在 Unity 的基础之上的。2D 版将驾驶 RigidBody2D，而 3D 版将驾驶 CharacterController。所以对于碰撞，你需要**碰撞器**，设置在你的角色和障碍物/地面/等上。

图层[](https://topdown-engine-docs.moremountains.com/collisions.html#layers)
--------------------------------------------------------------------------

该引擎依靠[层](https://docs.unity3d.com/Manual/Layers.html)来识别某些对象，特别是墙壁和代理。图层是您可以将游戏对象与之关联的元数据，然后您可以使用这些元数据仅通过图层蒙版（一组图层）将光线投射到某些图层上。请注意，图层和[排序图层](https://unity3d.com/learn/tutorials/topics/2d-game-creation/sorting-layers)是完全不同的东西。TopDown 引擎中的图层排序没有任何限制或命名约定。

这是引擎使用的主要层的列表。请注意，唯一强制性的是与平台相关的：

-   **Ground**：无论您是在 2D 还是 3D 环境中，这都标志着您的角色将被视为地面（和可行走）的碰撞体。在 2D 中并使用 tilemaps 时，将地面的 CompositeCollider2D 的 GeometryType 设置为 Polygons 非常重要。您可以在引擎的多个演示场景中看到一个示例，例如 Koala2D。
-   **障碍物**：碰撞器会阻止您的角色行走，如果他们在隧道中，则无法起身，也会阻止您的子弹。
-   **MovingPlatform**：您所有的移动平台。
-   **Enemies**：放置所有属于敌人的碰撞体（这会伤害并被你的角色伤害）
-   **洞**：仅适用于 2D，使用此标签标记碰撞体，角色会将它们视为可以落入的洞
-   **FallingPlatform**：适用于所有坠落平台
-   **Projectile** : 一个放置所有射弹碰撞器的层
-   **Player** : 放置玩家碰撞器的层
-   **ObstaclesDoors**：在 3D 门周围放置某些安全区域的特殊层，将该信息传达给寻路 AI
-   **NoPathfinding**：放置您希望寻路 AI 避免的碰撞器的层

这些层，就像在任何 Unity 项目中一样，依赖物理碰撞矩阵来确定它们可以交互或碰撞的层。您可以通过编辑 > 项目设置 > 物理（或 2D 控制器的 Physics2D）编辑碰撞矩阵。在那里你会看到一个复选框矩阵，只要确保你想要交互的两个层的交集被选中。例如，如果您希望您的播放器能够与其他播放器发生碰撞，请确保选中播放器/播放器复选框。

标签[](https://topdown-engine-docs.moremountains.com/collisions.html#tags)
------------------------------------------------------------------------

[标签](https://docs.unity3d.com/Manual/Tags.html)是您可以添加到游戏对象中的元数据，以便从其他脚本中更容易地找到它们。引擎根本不依赖标签。不过，请随时在您的脚本中继续使用它们！