用户界面
====

本页介绍 UI 在 TopDown Engine 中的工作原理。

-   [介绍](https://topdown-engine-docs.moremountains.com/ui.html#introduction)[](https://topdown-engine-docs.moremountains.com/ui.html#introduction)
-   [用户界面相机](https://topdown-engine-docs.moremountains.com/ui.html#ui-camera)[](https://topdown-engine-docs.moremountains.com/ui.html#ui-camera)
-   [游戏HUD](https://topdown-engine-docs.moremountains.com/ui.html#game-hud)[](https://topdown-engine-docs.moremountains.com/ui.html#game-hud)
-   [对话框](https://topdown-engine-docs.moremountains.com/ui.html#dialogue-boxes)[](https://topdown-engine-docs.moremountains.com/ui.html#dialogue-boxes)
-   [暂停屏幕](https://topdown-engine-docs.moremountains.com/ui.html#pause-screen)[](https://topdown-engine-docs.moremountains.com/ui.html#pause-screen)
-   [菜单](https://topdown-engine-docs.moremountains.com/ui.html#menus)[](https://topdown-engine-docs.moremountains.com/ui.html#menus)
-   [健康棒](https://topdown-engine-docs.moremountains.com/ui.html#healthbars)[](https://topdown-engine-docs.moremountains.com/ui.html#healthbars)

介绍[](https://topdown-engine-docs.moremountains.com/ui.html#introduction)
------------------------------------------------------------------------

虽然主要关注游戏玩法，但自上而下引擎在各处都包含**GUI**元素以与玩家进行交流。通常用作占位符（因为您可能会用自己的艺术/风格替换它们），了解它们的工作原理仍然很有用。

用户界面相机[](https://topdown-engine-docs.moremountains.com/ui.html#ui-camera)
-------------------------------------------------------------------------

引擎的大多数级别都有两个[摄像头](https://topdown-engine-docs.moremountains.com/cameras.html)：一个普通的 2D 或 3D 摄像头，以及一个**UI 摄像头**。后者负责显示游戏 HUD 和其他非世界视觉元素。如果您查看 UICamera 预制件，您会看到它也包含按钮、箭头、操纵杆、暂停启动画面、游戏结束画面等。所有这些都由 GUI 管理器控制，这是一个位于顶层的组件那个预制件。这些部分中的每一个都绑定到 GUI 管理器的检查器。

游戏HUD[](https://topdown-engine-docs.moremountains.com/ui.html#game-hud)
-----------------------------------------------------------------------

作为 UICamera 预制件的一部分，HUD 具有健康栏、头像，但也可以包括点数、级别名称和 FPS 计数器。所有这些都绑定到 GUIManager 并通过其各种方法进行更新。随意更改它们的外观、字体等。

对话框[](https://topdown-engine-docs.moremountains.com/ui.html#dialogue-boxes)
---------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/dialogue-1.png)

KoalaDungeon 演示场景中的经典对话示例

该引擎包含一个**非常简单的对话系统**，允许您在关卡中的任何位置显示单向对话或工具提示。要使用它，您只需要一个区域。区域只是一个带有 BoxCollider2D（或 BoxCollider，如果您是 3D 环境）的游戏对象，它决定了角色需要处于哪个区域才能激活区域。然后您所要做的就是**向其中添加一个 DialogueZone 组件**。该区域也可以附加到一个角色（只需将它嵌套在您的层次结构中的角色下方，它就会跟随它）。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/dialogue-2.png)

MinimalSandbox3D 演示场景中的 DialogueZone 检查器

一旦**DialogueZone**组件已添加，所有你需要做的是建立了督察。有许多与激活相关的复选框，可让您决定如何以及何时激活对话。您还可以决定显示提示（默认情况下是一个小的"A"图标，您可以随意替换为您想要的任何内容）。然后您可以通过调整文本和背景颜色或字体来更改对话框外观。在检查器的最底部是您可以定义对话线的地方。如果您有多个，它们**将按顺序**显示，从上到下。

您将在多个演示中找到对话区域的示例。如果您需要 2D 示例，请查看 KoalaDungeon 演示场景开头旁边的绿色字符。对于 3D，在 MinimalSandbox3D 中起始位置西北部的绿色字符上有一个。

暂停屏幕[](https://topdown-engine-docs.moremountains.com/ui.html#pause-screen)
--------------------------------------------------------------------------

在**暂停画面**是UICamera的子部分，包含黑色覆盖，一些文本和几个按钮。您当然可以（并且应该）自定义它以具有您自己的按钮和艺术风格。为此，您所要做的就是展开 UICamera 预制件，找到 PauseSplash 部分，然后在那里进行更改。

菜单[](https://topdown-engine-docs.moremountains.com/ui.html#menus)
-----------------------------------------------------------------

大多数菜单，例如开始或游戏结束屏幕，都基于 Nice Touch，就像移动控件一样。这允许非常简单的设置和跨平台功能，无论您是否针对基于触摸的设备。只需确保针对特定目标正确设置面板和触摸区（PC 应启用鼠标模式）。

血条[](https://topdown-engine-docs.moremountains.com/ui.html#healthbars)
-----------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/gui-1.png)

带有健康栏的忍者敌人的示例

**Healthbars**是您可以添加到任何带有 Health 组件的角色的组件。它将允许您在角色旁边显示一个进度条，显示其**当前的健康水平**。设置非常简单，但您将获得大量很酷的选项：您可以决定是更愿意使用 ProgressBar 预制件，还是让引擎绘制它。在这种情况下，您可以选择正面和背面颜色，决定填充和大小，以及相对于角色中心放置条的偏移量。你可以有一个延迟的酒吧，当健康水平改变时让它颠簸和闪烁。此外，您可以让它**始终可见**，或者仅在角色每次命中后的几秒钟内**可见**。