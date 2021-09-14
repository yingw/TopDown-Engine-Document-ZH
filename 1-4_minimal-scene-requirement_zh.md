最低场景要求
======

此页面涵盖了场景中引擎工作所需的所有游戏对象。

-   [介绍](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#introduction)[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#introduction)
-   [最小场景](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#minimal-scene)[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#minimal-scene)

介绍[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#introduction)
------------------------------------------------------------------------------------------------

在自顶向下引擎中，就像在大多数 Unity 项目中一样，关卡由场景组成。你可以在你的场景中添加很多东西（墙壁、敌人等），它可以很大，也可以很小，**这真的取决于你**。但是无论您做什么，引擎都需要一些要素才能工作。该引擎包括两个"最小"场景示例，3D 场景和 2D 场景。这些场景展示了"标准条件"的最小元素。从技术上讲，您甚至可以删除更多内容，但它们是很好的**起点**。

最小场景[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#minimal-scene)
---------------------------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/minimal-requirements.png)

最小场景的内容

您将在 Minimal2D 文件夹中找到一个起始 2D 场景的示例，在 Minimal3D 文件夹中找到一个 3D 场景的示例。两者都非常相似，唯一的区别在于它们使用的相机类型（一个是透视，另一个是正交）。这是它们包含的内容：

-   **GameManager**：GameManager 负责处理游戏循环。如果您想在引擎中使用大多数"游戏机制"类，它在每个场景中都是强制性的。
-   **SoundManager**：顾名思义，它是播放声音的中心点。这不是强制性的，但您可能希望拥有它。
-   **其他管理器**：**LevelManager**负责生成您的角色，并处理特定于关卡的内容。您必须指定此关卡使用的角色，以及其检查器中的初始生成点。该**InitialSpawnPoint**只是一个转换，告诉LevelManager那里产卵的第一个字符。该**TimeManager**将处理所有的时间操作为您服务。这适用于诸如放慢时间之类的高级内容，也适用于诸如暂停之类的简单内容。最后，**AchievementRules**是可选的，描述了在这个级别可以解锁哪些成就。
-   **相机**：通常你会希望在你的关卡中有一个相机。两个 Minimal 场景都带有高级相机设置、Cinemachine 虚拟相机和 UICamera 来支持您的 UI 元素。当然，您可以删除所有这些并使用简单的相机。请注意， UICamera 还包含**InputManager**。如果没有 InputManager，您的角色**将不会移动**。因此，如果您决定摆脱该 UICamera，请确保您的场景中某处有一个 InputManager。
-   **Level**：基本地面/墙壁。可选，应替换为您的。