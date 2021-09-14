资产的内容
=====

此页面描述资产的内容。

-   [介绍](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#introduction)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#introduction)
-   [常见的](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#common)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#common)
-   [演示](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#demos)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#demos)
    -   [考拉2D](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#koala2d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#koala2d)
    -   [爆炸](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#explodudes)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#explodudes)
    -   [草原](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#grasslands)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#grasslands)
    -   [关卡选择](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#levelselection)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#levelselection)
    -   [阁楼3D](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#loft3d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#loft3d)
    -   [最小二维](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal2d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal2d)
    -   [最小3D](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal3d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal3d)
    -   [开始画面](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#startscreen)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#startscreen)
-   [第三者](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#thirdparty)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#thirdparty)

介绍[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#introduction)
-------------------------------------------------------------------------------------------

当您将资产导入您的项目时，您将获得一个 TopDownEngine 文件夹，其中包含三个子文件夹。我建议保留该文件夹原样，**不要修改其内容**。相反，为您的游戏资产创建一个专用文件夹，如果您需要修改代码，只需将 TopDown Engine 的类扩展到您的类中即可。如果您想了解更多相关信息，请查看["继承"部分](https://topdown-engine-docs.moremountains.com/creating-your-own-game.html#inheritance)。这是这四个文件夹的内容以及一般文件夹结构的概要。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/contents-1.png)

资产内容

常见的[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#common)
--------------------------------------------------------------------------------------

顾名思义，Common 包含引擎工作所需的所有脚本和视觉资产。您需要在游戏中保留该文件夹。主要结构由以下文件夹组成：

-   **动画**：所有常见的动画（主要是 GUI 的东西）。
-   **字体**：各种 GUI 屏幕中使用的字体存储在那里。
-   **PhysicsMaterials**：大多数演示中使用的一些物理材料，但不特定于任何材料。
-   **预制件**：在各个演示关卡中使用的所有预制件。
-   **资源**：直接通过代码实例化的预制件。
-   **脚本**：引擎的"核心"，也是其大部分价值所在。我们将在一分钟内讨论详细信息。
-   **Sprites**：所有演示共有的所有精灵。同样，主要是 GUI 的东西。

Scripts 文件夹是存储所有引擎脚本的地方。每个演示可能有一个或多个特定的脚本，但除此之外，它就在那里的某个地方。请注意，MMTools 脚本位于另一个根文件夹中，以便于维护和更好的逻辑分离。以下是主要的 Scripts 文件夹：

-   **成就**：主要是成就规则，其余的成就脚本在 MMTools 中，如果您发现自己正在寻找它们。
-   **相机**：各种相机相关的脚本
-   **角色**：在这里你会找到让角色移动和行动的所有脚本。从控制器、角色能力到 AI 脚本和武器。
-   **环境**：从掉落块到传送器，您将在此文件夹中找到处理关卡对象的大部分脚本。
-   **GUI**：顾名思义，在这里您可以找到与 GUI 相关的所有内容：级别选择器、暂停屏幕等。
-   **物品**：硬币或可拾取的武器可以在此文件夹中找到。
-   **管理器**：所有管理器（"超级"类，通常是单例，处理全局的东西）都在这个里面。
-   **Spawn**：所有特定于 spawn 的脚本都在那里。

演示[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#demos)
------------------------------------------------------------------------------------

Demos 文件夹包含引擎中包含的所有演示。它们按"宇宙"分组，每个宇宙可能包含一个或多个场景。通常每个演示旨在展示**引擎的一个或多个特定方面**，或者如何通过一些调整和不同的艺术来获得不同的结果。

### 考拉2D[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#koala2d)

-   **KoalaDungeon**：一个关于引擎可以在 2D 中做什么的"完整"演示

### 爆炸[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#explodudes)

-   **爆炸**：炸弹人风格的 4 人 3D 演示。投下炸弹，在网格上移动，打破板条箱和你的对手。这个场景带有自己的起始画面、可选的电源ups和所有炸弹人的核心机制。

### 草原[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#grasslands)

-   **草原**：4 人多人游戏的 2D 演示。您可以选择一种相机模式（分屏或分组拍摄），然后玩家竞争以在 1 分钟内获得最多的硬币，或者成为最后一个站立的玩家。

### 关卡选择[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#levelselection)

-   **LevelSelection**：基于轮播的关卡选择屏幕

### 阁楼3D[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#loft3d)

-   **Loft3D**：迈阿密热线启发的 3D 场景

### 最小二维[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal2d)

-   **Minimal2D**：快速启动 2D 场景的最低要求
-   **Minimal2Drooms1**：如何将房间链接在一起的示例
-   **Minimal2Drooms2**：该示例的第二部分
-   **MinimalSandbox2D**：一个场景，展示了您可以放在 2D 场景中的大部分功能
-   **Minimal2DGrid**：这个场景演示了如何在 2D 中实现基于网格的移动

### 最小3D[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal3d)

-   **MinimalAI3D**：高级 AI 行为示例
-   **MinimalPathfinding3D**：展示如何在引擎中使用寻路的场景
-   **MinimalSandbox3D** : 一个包含可以在您自己的 3D 场景中使用的功能的场景
-   **MinimalScene3D**：快速启动 3D 场景的最低要求
-   **MinimalSword3D**：一个演示场景，展示了一个基于 3D 组合的剑挥舞角色，与视锥引导的 AI 对抗
-   **Minimal3DGrid**：这个场景演示了如何在 3D 中实现基于网格的移动

### 开始画面[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#startscreen)

-   **开始屏幕**：一个开始**屏幕**的例子，带有一个选项弹出窗口和人工智能背景

第三者[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#thirdparty)
------------------------------------------------------------------------------------------

第三方包含不直接特定于自上而下引擎的脚本和资源。

-   该**库存引擎**被更多的山，通常单独销售，而是包含在自上而下的引擎作为礼物另一项资产。顾名思义，它将有助于创建和自定义库存。
-   **MMInterface**是 More Mountains 的库和资源，旨在加快在 Unity 中创建 UI 屏幕的过程。
-   该**MMTools**都是在所有多仙山资产使用佣工和小班。其中一些可能不会在自上而下引擎中使用，但我建议**不要删除它们**。未使用的不会使您的构建更重，因此保留它们更安全、更简单。本文档没有详细介绍它们，但如果您有兴趣，它们都会被注释并在 API 文档中进行解释。
-   该**MMToolsForThirdParty**是针对驾驶或富集是尚未建成统一的API，如Cinemachine或后处理堆栈更多山脚本。
-   **NavmeshComponents**：来自 https://github.com/Unity-Technologies/NavMeshComponents，一旦可用，将被包依赖替换
-   **Tilemap**：来自 https://github.com/Unity-Technologies/2d-extras/tree/master/Assets/Tilemap/Brushes，一旦可用，将被包依赖替换