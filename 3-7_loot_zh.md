抢劫
==

本页描述了战利品系统的工作原理。

-   [介绍](https://topdown-engine-docs.moremountains.com/loot.html#introduction)[](https://topdown-engine-docs.moremountains.com/loot.html#introduction)
-   [定义你的战利品表](https://topdown-engine-docs.moremountains.com/loot.html#defining-your-loot-table)[](https://topdown-engine-docs.moremountains.com/loot.html#defining-your-loot-table)
-   [在我的游戏中添加战利品](https://topdown-engine-docs.moremountains.com/loot.html#adding-loot-to-my-game)[](https://topdown-engine-docs.moremountains.com/loot.html#adding-loot-to-my-game)
-   [战利品系统更进一步](https://topdown-engine-docs.moremountains.com/loot.html#going-further-with-the-loot-system)[](https://topdown-engine-docs.moremountains.com/loot.html#going-further-with-the-loot-system)

介绍[](https://topdown-engine-docs.moremountains.com/loot.html#introduction)
--------------------------------------------------------------------------

大多数游戏以一种或另一种形式向玩家随机分配某些行动的奖励。在自上而下的游戏中，敌人死亡时经常会掉落战利品。迈阿密热线的敌人会掉落他们的武器，暗黑破坏神怪物会掉落随机的金币和物品，箱子可能包含随机奖励等。自上而下引擎将让您轻松实现类似的随机**战利品系统**。它是**通用的**，这意味着你可以用它来实现各种需要受控随机性的系统：战利品箱、关卡生成、NPC 统计数据创建、类似无主之地的武器生成器等。围绕**战利品表**设计模式构建，如Daniel Cook 于 2014 年[在他的博客中](https://lostgarden.home.blog/2014/12/08/loot-drop-tables/)详细描述[了](https://lostgarden.home.blog/2014/12/08/loot-drop-tables/)，这个系统简单而强大，应该为您的游戏打开大量的可能性。

定义你的战利品表[](https://topdown-engine-docs.moremountains.com/loot.html#defining-your-loot-table)
--------------------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/loot-1.png)

Loft3DLootTable 脚本化对象

在实际掉落战利品之前你要做的第一件事是定义**战利品定义**. 战利品定义是一个可编写脚本的对象（一个数据文件），它将保存有关哪些对象构成您的战利品表以及获得每个对象的机会的信息。要创建一个，在项目的任何文件夹中，右键单击 > 创建 > 更多山脉 > 战利品定义。接下来，定义你的战利品表应该包含多少个物体，对于每个物体，拖动你想要在战利品掉落时产生的物体的预制件，并指定它们各自的权重。权重是相互关联的，它们不必加起来就是任何特定的数字。如果您有 3 个对象 A、B 和 C，并且希望 C 掉落的次数比其他对象多 10 倍，您可以不加选择地使用以下权重：A:1,B:1,C:10，或者您可以使用 A： 2,B:2,C:20。

在我的游戏中添加战利品[](https://topdown-engine-docs.moremountains.com/loot.html#adding-loot-to-my-game)
---------------------------------------------------------------------------------------------

要在游戏中放置这些对象，您可以使用 Loot 组件。它旨在与 Health 组件结合使用，让您在死亡或损坏时触发战利品掉落。或者，它可以自动使用，您所要做的就是调用它的 SpawnLoot 公共方法，它就会掉落战利品。

例如，您可以选择一个敌人，并为其添加 Loot 组件。在其检查器中，您将能够自定义其行为：

-   战利品**模式**：Unique 将让您生成单个对象，Loot Table 将让您定义一个本地战利品表（仅针对此特定敌人/对象），而 Loot Table Scriptable Object 将让您绑定一个战利品定义，如以上部分。
-   **条件**：让您决定是否希望战利品在死亡或损坏（或两者）时发生。这需要一个 Health 组件。
-   该**菌种**部分让你定义一个延迟（以秒），对象菌种任选随机量，以及先进的**产卵特性**。
-   **生成属性**：在这里您可以定义生成对象将在其中实例化的区域的形状。您需要特别注意 NormalToSpawnPlane，它定义了对象将在其中实例化的平面。通常对于 3D，您将使用 0,1,0 和 2D 0,0,1。Spawn Properties 还可以让您指定偏移、半径、随机旋转和缩放。
-   **碰撞**：一个选项让战利品系统在生成物体之前检查碰撞（例如，避免武器选择器出现在墙中间）。
-   **反馈**：与引擎中的大多数系统一样，您可以在本机中插入一个[MMFeedbacks](https://topdown-engine-docs.moremountains.com/feedback.html)，它会在每次战利品对象掉落时在生成位置播放。
-   **调试**：此部分允许您在运行时生成大量对象，以检查它们的位置以及结果是否与您定义战利品表时的想法相符。一个选项还允许您绘制显示放置区域的小工具。

战利品系统更进一步[](https://topdown-engine-docs.moremountains.com/loot.html#going-further-with-the-loot-system)
-------------------------------------------------------------------------------------------------------

该系统的核心是**MMLootTable**类。它是一个通用类，定义了要"掠夺"或挑选的对象列表，每个对象都加权。它有两个简单的方法：**ComputeWeights**，你通常只在初始化时调用一次，以及**GetLoot**，它将返回一个对象，从表中随机选择。如果您想选取多个对象，只需重复该操作即可。在上面的示例中，我们为游戏对象执行此操作，但此类是通用的，您可以为其他任何内容执行此操作。该引擎带有现成的 MMLootTableFloat（用于浮点数）和 MMLootTableString（用于字符串）实现，您当然可以添加更多来满足您的特定需求。