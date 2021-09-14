如何创建自己的角色？
==========

本页介绍了角色在自上而下引擎中的功能以及如何构建自己的角色。

-   [介绍](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#introduction)[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#introduction)
-   [基本概念](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#base-concepts)[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#base-concepts)
-   [等级制度](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#hierarchy)[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#hierarchy)
-   [如何创建代理？](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#how-do-i-create-an-agent-)[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#how-do-i-create-an-agent-)
    -   [自动创建](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#automatic-creation)[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#automatic-creation)
    -   [复制](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#copy)[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#copy)
    -   [组件方法](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#components-approach)[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#components-approach)

介绍[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#introduction)
---------------------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/howtocharacter-1.png)

一个典型的可玩角色，Loft3D 演示中的吊带角色

自上而下引擎中的"**代理**"是一个术语，用于描述任何类型的角色，无论他们是可玩角色，还是敌人、NPC 等。有一些[核心类](https://topdown-engine-docs.moremountains.com/character-classes.html)可以使这些代理工作，您将需要这些[类](https://topdown-engine-docs.moremountains.com/character-classes.html)例如，熟悉是否要扩展和创建更多角色能力。

同时，此页面旨在展示**基本概念**并允许您快速创建自己的角色（玩家控制或基于 AI）。

基本概念[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#base-concepts)
------------------------------------------------------------------------------------------------

自顶向下引擎设计**用于 2D 和 3D 项目**。您将用于为一种设置或另一种设置创建角色的组件将大体相同，但有些将特定于 2D 或 3D。当您遇到一个组件或一项能力时，如果它的名称中没有 2D 或 3D，则可以安全地假设它对两者都适用。否则，您将希望将名称中带有 2D 的组件仅用于 2D，而名称中带有 3D 的组件仅用于 3D。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/howtocharacter-2.png)

角色上常见的组件堆栈示例，在本例中为 3D 角色

[此页面](https://topdown-engine-docs.moremountains.com/character-classes.html)详细介绍了有关角色的必需组件的更多详细信息，但这里有一个**简要概述**。自顶向下引擎中的代理通常具有以下组件：

-   **碰撞器**：2D 中的 BoxCollider2D 或 CircleCollider2D，3D 中的 CharacterController，此碰撞器的大小用于确定碰撞以及代理在世界中的位置。
-   **RigidBody2D 或 3D**：仅用于提供与标准物理的基本交互（完全可选）
-   **TopDownController**：负责碰撞检测、基本运动（向左/向右移动）、重力，TopDownController 是您角色的电机类。它有 2D 和 3D 版本，但都具有相同的方法和逻辑。请注意，3D 版本需要 CharacterController 组件。
-   **角色**：这是连接所有其他类的中心类。它本身并没有什么作用，但确实充当了一个中心点。这就是你定义玩家是人工智能还是玩家控制的地方，它的模型和动画师在哪里，诸如此类。它也是在运行时控制所有角色能力的类。
-   **健康**：不是强制性的，但在大多数游戏中，您的代理将能够死亡。Health 组件处理伤害、健康获得/损失以及最终的死亡。
-   **角色能力**：到目前为止，所有以前的组件都提供了很多可能性，但并没有真正"做"任何可见的事情。这就是角色能力的用途。该资产包含超过 15 种能力，从简单的如 CharacterMovement 到更复杂的如武器处理。它们都是可选的，您可以选择任何您想要的。您当然也可以轻松创建自己的能力来构建自己的游戏。

等级制度[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#hierarchy)
--------------------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/howtocharacter-6.png)

推荐的 Characters 层次结构

无论您如何创建角色，真正重要的一件事是了解如何构建角色。你要**分开**的**逻辑**从（在刚体，TopDownController，角色能力等），**视觉**（模型/精灵/脊柱设置等）。您可以拥有更多层（也许您的动画师位于其自己的层上，等等），但推荐的设置是上图中的设置：具有所有逻辑的顶层，以及嵌套在其中的模型。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/howtocharacter-7.png)

让 Character 组件知道 Animator 和 Model 的位置

确保从检查器将模型链接到角色类，动画师也是如此。其他一些类（定向能力、健康）也可能要求您通过他们的检查员告诉他们模型或动画师的位置。

如何创建代理？[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#how-do-i-create-an-agent-)
---------------------------------------------------------------------------------------------------------------

有**很多方法**可以创建在自上而下的引擎可播放或AI角色。在这里，我们将介绍**3 个推荐的**。请注意，如果您更喜欢做不同的事情，只要它适合您，一切都很好。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/howtocharacter-3.png)

您可以使用 AddComponent 菜单添加大多数 TopDown Engine 的组件（不仅仅是 Character 组件）

### 自动创建[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#automatic-creation)

"自动**构建角色**"功能可让您在几秒钟内创建一个新角色。请注意，在初始设置之后，您仍然需要设置动画等等。

以下是如何进行：

![杰基尔](https://topdown-engine-docs.moremountains.com/images/howtocharacter-4.png)

自动构建按钮

**对于 3D ：**

1.  打开 MinimalScene3D 演示场景（或任何满足[最低要求的](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements)场景）[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements)
2.  创建一个*空的*游戏对象，命名为"Test"，位置在 0,0.5,0
3.  在它下面，添加一个立方体，居中，将其缩放到 1,2,1，移除它的 BoxCollider
4.  在测试中，添加一个**Character** comp，将 Cube 拖动到其*CharacterModel*插槽中
5.  在角色检查器上，按**Autobuild Player Character 3D**
6.  按播放 ![:tada:](https://github.githubassets.com/images/icons/emoji/unicode/1f389.png ":tada:")

**对于 2D ：**

1.  打开 Minimal2D 演示场景（或任何满足[最低要求的](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements)场景[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements)
2.  创建一个*空的*游戏对象，将其命名为"Test"，将其放置在场景中
3.  在它下面，添加一个游戏对象，居中，将其命名为"模型"，为其添加一个精灵渲染器并设置其精灵
4.  在测试中，添加一个**角色**组合，将精灵拖到其*CharacterModel*插槽中
5.  在角色检查器上，按**Autobuild Player Character 2D**
6.  按播放 ![:tada:](https://github.githubassets.com/images/icons/emoji/unicode/1f389.png ":tada:")

当然，对于 AI 来说也是一样的，除了你会选择 Autobuild AI Character 2D/3D。如果你选择了一个 AI 角色，它已经准备好获得[一个大脑和一些动作和决策](https://topdown-engine-docs.moremountains.com/advanced-ai)。您现在可以微调各种设置，**删除您**对该角色**不感兴趣的能力**，添加[动画](https://topdown-engine-docs.moremountains.com/animations)等。或者您可以保持原样并**开始**为您的游戏和关卡的其余部分制作**原型**。

### 复制[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#copy)

创建代理的另一种快速方法是在演示中找到您喜欢的代理，然后**从中创建您**的代理。过程非常简单：

![杰基尔](https://topdown-engine-docs.moremountains.com/images/howtocharacter-5.png)

复制现有的预制件

1.  在其中一个演示中**找到您喜欢的代理**。
2.  **找到它的预制件**（在场景视图中选择代理，在它的检查器中，在预制件名称和标签下的右上角有一个选择按钮）
3.  **复制预制件**(cmd + D)
4.  **将其重命名**为您希望角色被称为的任何名称
5.  **进行您想要的更改。**也许您只想替换一些设置，也许您想更改精灵和动画。这取决于你。

### 组件方法[](https://topdown-engine-docs.moremountains.com/how-to-create-character.html#components-approach)

您还可以**从头开始创建角色**。它更长，但为什么不呢？

1.  从一个**空的游戏对象**开始。理想情况下，您需要将字符部分与视觉部分分开。最好的层次结构在顶层有 TopDownController/Collider/Character/Abilities，然后嵌套可视部分（精灵、模型等）。
2.  在检查器的顶部，如果是玩家角色，**则将标签设置为 Player，**如果不是，则**设置为**您喜欢的任何内容。图层也是一样。
3.  在您的顶级对象上，添加一个**碰撞器**（2D 或 3D，我们建议为 3D 角色使用 Capsule，为 2D 角色添加一个框）。调整其大小以匹配您的精灵/模型尺寸。然后添加一个 RigidBody2D 或 RigidBody 组件。
4.  添加**TopDownController**（2D 或 3D）组件。设置各种设置（如果您需要帮助，请参阅类文档），并确保设置各种碰撞掩码（平台、一种方式等）。如果您要使用 3D，也添加一个**CharacterController**组件。
5.  添加一个**字符**组件。检查各种设置以确保它们适合您。
6.  添加您想要的**角色能力**（最好使用检查器底部的 AddComponent 按钮，然后导航到那里）
7.  或者，添加**Health**组件、**HealthBar**组件等。