移动平台
====

本页解释了如何在自上而下引擎中创建移动平台。

-   [介绍](https://topdown-engine-docs.moremountains.com/moving-platforms.html#introduction)[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#introduction)
-   [打造移动平台](https://topdown-engine-docs.moremountains.com/moving-platforms.html#creating-a-moving-platform)[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#creating-a-moving-platform)
-   [设置移动平台](https://topdown-engine-docs.moremountains.com/moving-platforms.html#setting-up-moving-platforms)[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#setting-up-moving-platforms)

介绍[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#introduction)
--------------------------------------------------------------------------------------

在自上而下引擎中创建**移动平台**非常简单，但您可以使用它们做很多事情，并且有很多方法可以根据您的独特需求调整它们。有关移动平台的示例，您可以查看 KoalaDungeon 演示关卡的右下方房间。MinimalSandbox3D 场景中也有一个。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/moving-platform-1.png)

KoalaDungeon 演示关卡中的移动平台示例

打造移动平台[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#creating-a-moving-platform)
--------------------------------------------------------------------------------------------------------

要创建一个移动平台，只需遵循以下简单步骤：

-   首先在场景中拖动精灵或 3D 模型
-   选择您新创建的游戏对象，并将其图层设置为"MovingPlatforms"
-   向其添加非触发 BoxCollider2D 或 BoxCollider（取决于您使用的是 2D 还是 3D 角色）
-   向其添加 Rigidbody 或 RigidBody2D 组件，将其设置为 kinematic
-   向您的对象添加一个 MovingPlatform2D 或 MovingPlatform3D 组件。
-   你完成了！剩下要做的就是调整MovingPlatform 组件的检查器。

设置移动平台[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#setting-up-moving-platforms)
---------------------------------------------------------------------------------------------------------

在MovingPlatform 的检查器中，您可以调整一些内容。

首先是**路径**部分。您可以先决定一个**Cycle Option**。您可以选择来回（1 > 2 > 3 > 2 > 1 > 2 等）、循环（1 > 2 > 3 > 1 > 2...）和仅一次（1 > 2 > 3）。然后是循环初始移动方向，根据您的选择，它将从路径中的第一个（上升）点或最后一个（下降）点开始移动。然后当然还有实际的**路径元素**，您需要在其中指定数组的大小。从那里，您可以输入点坐标，也可以简单地将平台旁边出现的小手柄拖放到您选择的位置。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/moving-platform-2.png)

在 MinimalSandbox3D 场景中定位移动平台的路径元素

一旦您对它们的位置感到满意，您就可以返回检查器，并设置移动**速度**和**加速类型**。MinDistanceToGoal 字段最好保留其默认值，但如有必要，请随意更改它。